# Pokémon Emerald pseudocode reference

The clean Emerald decompilation gives us readable C, event scripts, tables, and assets. The uploaded Expanded ROM contains compiled ARM and Thumb instructions and modified data. Its verified offsets are in EM-12. The other sections describe the clean source at commit `9103e529c2fbdd7add4a1ff3350c6c1f92112c42`. This is a subsystem reference. It condenses the main execution paths and records where to inspect their branches and exceptions.

To refer to a section in chat, use its ID and, if relevant, a symbol or address. For example, ask “In **EM-03**, where would we change the level of Reedwake's starter?” or “In **EM-12**, trace the call at `0x09FFC3B2`.”

| ID | System | What you can trace |
| --- | --- | --- |
| [EM-01](#em-01-boot-and-frame-loop) | Boot and frame loop | How the active screen takes control |
| [EM-02](#em-02-new-game-and-overworld) | New game and overworld | Where the player spawns and how the field updates |
| [EM-03](#em-03-starter-selection) | Starters | The menu, the gift, and the first battle |
| [EM-04](#em-04-maps-and-event-scripts) | Maps and scripts | Warps, triggers, and event state |
| [EM-05](#em-05-wild-encounters) | Wild Pokémon | How map data becomes a battle |
| [EM-06](#em-06-battle-turn-and-move-resolution) | Battles | Turn actions, move scripts, and damage |
| [EM-07](#em-07-species-records-and-stats) | Pokémon data | Species records, individuals, and stat formulas |
| [EM-08](#em-08-evolution) | Evolution | How an event selects an evolution target |
| [EM-09](#em-09-sprites-and-palettes) | Graphics | Front, back, icon, and palette lookup |
| [EM-10](#em-10-gym-progression) | Gyms | Where a win becomes a badge and progression state |
| [EM-11](#em-11-saving-and-data-encoding) | Saves | Flash slots, checksums, and field encoding |
| [EM-12](#em-12-expanded-rom-hook) | Expanded ROM | Verified starter table and disassembled hook |

## EM-01 Boot and frame loop

`AgbMain` sets up the hardware-facing services. Callbacks turn the same main loop into a title screen, an overworld, or a battle. Tasks let a process continue in smaller steps across frames.

```text
boot:
    initialize hardware, input, audio, interrupts, flash detection, and callbacks
    initialize backgrounds, fonts, and heap

repeat:
    read buttons
    handle the soft reset chord when enabled
    update link state and dispatch active main callbacks
```

[Main loop @ src/main.c:89](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/main.c#L89-L180) · [Task scheduler @ src/task.c:110](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/task.c#L110)

## EM-02 New game and overworld

`CB2_NewGame` sets the initial field callback to the moving-truck sequence. The first overworld callback handles field input while the regular overworld screen is active. The second controls the field update and rendering work.

```text
new_game:
    clear field interrupts and stop map music
    initialize new save state, player avatar, play clock, and script context
    set the opening field callback to the moving-truck sequence
    load the initial map and install the overworld callbacks

overworld_update:
    advance any active event script
    run scheduled tasks and animate sprites
    update camera and sprite attributes
    update palette fades, tileset animations, and pending background copies
```

[New game data @ src/new_game.c:149](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/new_game.c#L149) · [Field callbacks and initialization @ src/overworld.c:1459](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/overworld.c#L1459-L1548)

## EM-03 Starter selection

The menu returns a zero-based choice index. The gift callback stores that index in `VAR_STARTER_MON` and resolves the species through `GetStarterPokemon`. Changing the selection table changes the choices. The level comes from the gift callback.

```text
choices = [Treecko, Torchic, Mudkip]

enter starter menu with give_starter as the return callback
while browsing:
    left or right changes the index within bounds
    A opens the selected Pokémon's picture and confirmation prompt
    No or B returns to browsing
    Yes saves the selected index and resumes give_starter

give_starter:
    VAR_STARTER_MON = selected_index
    give choices[selected_index] at level 5 with no held item
    start the transition to the first battle
```

[Choice table, species lookup, and UI @ src/starter_choose.c](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/starter_choose.c#L110-L118) · [Selection callbacks @ src/starter_choose.c:474](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/starter_choose.c#L474-L557) · [Gift and first battle @ src/battle_setup.c:910](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/battle_setup.c#L910-L947)

## EM-04 Maps and event scripts

A map definition connects a layout to its neighbors, doors, NPCs, and trigger coordinates. A trigger can require a particular variable value. The field interpreter dispatches commands and can yield while an action such as movement or dialogue finishes.

```text
when a field event activates:
    put the event's bytecode address in the script context
    lock normal field controls

on a field update with a running script:
    execute commands until a wait yields or the script ends
    if the script finishes:
        shut down the context
        unlock normal field controls

to choose a conditional map script:
    scan entries in order
    return the first script whose two variable values match
    return no script at the table terminator
```

[Example map definition @ data/maps/LittlerootTown/map.json](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/data/maps/LittlerootTown/map.json) · [Field script lifecycle and map hooks @ src/script.c](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/script.c#L55-L197) · [Command handlers @ src/scrcmd.c](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/scrcmd.c)

## EM-05 Wild encounters

This is the ordinary grass path. Surfing, fishing, the Safari Zone, and Battle Frontier areas have separate branches. The map's encounter table supplies species and level ranges. The slot-selection code supplies the odds of selecting each entry.

```text
on an eligible grass step:
    stop if encounters are disabled or the map has no land encounter table
    apply checks for entering a new metatile and passing the encounter rate roll
    if a roaming encounter is selected:
        start it if its level is allowed by Repel
        stop here either way
    if an outbreak encounter is selected and can be generated:
        start its battle
    otherwise:
        choose a weighted land encounter entry
        choose a level and apply the applicable ability and Repel checks
        start a wild battle if generation succeeds
```

[Map encounter tables @ src/data/wild_encounters.json](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/wild_encounters.json) · [Weighted slot selection](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/wild_encounter.c#L182) · [Generation](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/wild_encounter.c#L422) · [Standard encounter path](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/wild_encounter.c#L552-L630)

## EM-06 Battle turn and move resolution

The battle engine schedules actions. Each move effect has a script that calls C handlers. The following is the ordinary hit script. Specialized moves and effects can run a different script or enter the hit script partway through.

```text
for each scheduled action:
    dispatch its battle action handler
    for a move, execute its effect script

ordinary hit:
    check whether the move can proceed and whether it hits
    announce the move and deduct PP along the selected hit or miss path
    on a hit:
        calculate critical status, base damage, type effects, and final adjustment
        play the attack animation
        update the target's health bar and stored HP
        display the result, apply any secondary effect, and check for fainting
    run end-of-move processing
```

[Action dispatcher @ src/battle_main.c:4937](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/battle_main.c#L4937) · [Hit and miss scripts @ data/battle_scripts_1.s:236](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/data/battle_scripts_1.s#L236-L281) · [Damage and type commands @ src/battle_script_commands.c:1290](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/battle_script_commands.c#L1290-L1425)

## EM-07 Species records and stats

A species record supplies base stats and shared traits. An individual adds its own experience, personality, original trainer ID, IVs, EVs, and moves. The formulas below use integer division at each division step.

```text
create individual:
    initialize its boxed record for the species and requested level
    set the party-level data and calculate its battle stats

recalculate stats:
    level = look up level from experience and the species growth curve
    scaled = ((2 * base_stat + IV + EV / 4) * level) / 100
    maximum_HP = scaled_for_HP + level + 10, or 1 for Shedinja
    other_stat = apply_nature(scaled + 5)
    initialize HP for a new individual or adjust living HP by the max-HP change
    preserve fainted status for an existing fainted individual
```

[Species records](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/pokemon/species_info.h) · [Creation @ src/pokemon.c:2195](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/pokemon.c#L2195) · [Stats @ src/pokemon.c:2823](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/pokemon.c#L2823-L2895)

## EM-08 Evolution

The engine evaluates the current species' evolution entries in the context of an event such as leveling up, using an item, or trading. Conditional entries can inspect level, friendship, stats, held items, personality, and other state.

```text
on an evolution check:
    look up the current species' entries
    evaluate methods applicable to the requested evolution mode
    return the selected target species, or no target

when the caller starts the evolution scene:
    animate the change and handle cancellation when the caller allows it
    on success, apply the target and refresh the individual
```

[Evolution table](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/pokemon/evolution.h) · [Target selection @ src/pokemon.c:5503](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/pokemon.c#L5503) · [Evolution scene @ src/evolution_scene.c:209](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/evolution_scene.c#L209)

## EM-09 Sprites and palettes

Battle pictures, party icons, and overworld characters have independent asset tables. A new front picture still needs a matching palette and compatible animation frames. A party icon has its own palette lookup.

```text
show a battle Pokémon:
    use species and view to select the front or back picture
    decompress indexed pixels and apply any species-specific drawing behavior
    resolve the palette from species, trainer ID, and personality
    load the picture and palette for the battle sprite

show a party icon:
    resolve the icon tiles and icon palette
    create a sprite with the requested callback and position
```

[Battle graphics @ src/battle_gfx_sfx_util.c:600](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/battle_gfx_sfx_util.c#L585-L690) · [Picture and palette tables](https://github.com/pret/pokeemerald/tree/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/pokemon_graphics) · [Party icons @ src/pokemon_icon.c:1028](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/pokemon_icon.c#L1028) · [Overworld object graphics](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/object_events)

## EM-10 Gym progression

Roxanne's first battle illustrates how a gym win affects later events. The badge and TM have separate flags, so a full bag can delay the TM without taking away the badge.

```text
talk to the leader:
    start the first trainer battle if it is still pending
    otherwise check for a rematch or an unclaimed reward

on first victory:
    show badge text and play the badge fanfare
    set the gym-defeated flag and badge flag
    update the local city state and advance Petalburg's gym state
    update gym trainers and check the Petalburg unlock condition
    try to give the TM
    if the bag is full, leave the TM-received flag clear for a later visit
```

[Roxanne's script @ data/maps/RustboroCity_Gym/scripts.inc:4](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/data/maps/RustboroCity_Gym/scripts.inc#L4-L34) · [Trainer roster](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/trainers.h) · [Trainer parties](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/data/trainer_parties.h)

## EM-11 Saving and data encoding

Normal saves copy party and field objects into save data and write a full slot. The flash reader checks sector metadata and checksums when choosing a usable slot. The save engine also has smaller writes for specific modes.

```text
save normally:
    copy party and field objects into the save blocks
    advance the save counter and rotate the starting sector
    write the full slot
    if any sector write fails:
        restore the previous in-memory counter and sector index

load normally:
    check that flash is present
    select and load a valid slot into RAM
    restore the party and field objects

transform each secure boxed Pokémon word:
    word = word XOR personality XOR original_trainer_ID

change the save key on a protected field:
    field = field XOR old_key XOR new_key
    use the appropriate key width for a 16- or 32-bit field
```

The boxed record has a separate checksum and personality-dependent substructure order. Save counters, sector checksums, and field encoding are separate mechanisms.

[Slot writer and recovery @ src/save.c:139](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/save.c#L139-L176) · [Slot validation @ src/save.c:515](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/save.c#L515) · [Load path @ src/save.c:872](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/save.c#L872) · [Boxed record transformation @ src/pokemon.c:3536](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/pokemon.c#L3536-L3555) · [Save field rekeying @ src/load_save.c:274](https://github.com/pret/pokeemerald/blob/9103e529c2fbdd7add4a1ff3350c6c1f92112c42/src/load_save.c#L274-L293)

## EM-12 Expanded ROM hook

This section refers to the uploaded `Pokemon - Emerald Version (U) - Expanded.gba`, SHA-256 `439af4dc207873e8aab50370fb7879ca2d24b87f8669102a676a2c556ccf1b53`. The file is 32 MiB. The 16-bit starter entries `277, 280, 283` start at file offset `0x005B1DF8`. They are the stock internal species IDs for Treecko, Torchic, and Mudkip.

A Thumb branch at file offset `0x000E4530` loads the literal `0x09FFC3A1` from `0x000E4534` and branches to it. The CPU clears bit zero when selecting the Thumb instruction address, so the code starts at `0x09FFC3A0`, file offset `0x01FFC3A0`. The pseudocode preserves the observed byte operations and register-based calls. Their game-specific purpose remains unverified.

```text
hook:
    if r4 == 0:
        r4 = read_word(address loaded from literal at 0x09FFC3D0)
        status = read_byte(literal at 0x09FFC3D4 + r4)
        if status == 1:
            result = call target from literal at 0x09FFC3D8 via BX r0
            if result == 0:
                write byte 4 to (literal at 0x09FFC3DC + r4)
        tail-branch to target from literal at 0x09FFC3E0
    else:
        call target from literal at 0x09FFC3E4 via BX r1, with r0 = 2
        tail-branch to target from literal at 0x09FFC3E8
```

Here “literal at address” denotes the 32-bit value stored there. The stock source references above describe the clean engine. Changes unique to the expanded build need their own offsets and call traces.
