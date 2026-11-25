# Scientific-Fantasy Visual Direction

## Working identity

**Reedwake: The Resonant Tide** keeps the existing Vaelwater campaign and recasts its world as a scientific-fantasy region. Old waterworks, observatories, and relay stations were built to measure and guide a natural energy that moves through the watershed. The technology feels handmade and field-worn; the mystery remains older than the instruments used to study it.

The desired effect is a world that feels recognizably Pokémon at a glance—routes, towns, trainers, wild encounters, gyms, and a growing Pokédex—while its places, interfaces, and story have a distinct visual identity.

## Visual language

- **Palette:** midnight indigo and deep river blue for night and depth; bracken green and mineral teal for the landscape; luminous cyan for measured energy; restrained brass and parchment for instruments, maps, and records.
- **Materials:** carved stone, glazed ceramic, weathered copper, reed paper, glass sample jars, and cloth field markers.
- **Motifs:** tidal contour lines, star bearings, specimen diagrams, relay sigils, flood marks, and circular gauge faces. Use them as readable map and interface details, not as decoration on every surface.
- **Lighting:** warm lantern pools in inhabited places; cool cyan glows only near active relays, unusual Pokémon, or concentrated resonance.
- **Pixel-art rule:** keep silhouettes bold and colors purposeful at GBA scale. New visual detail must remain readable at 240 × 160 and within the engine's tile, palette, and sprite limits.

## Region treatment

Vaelwater's existing districts already support a coherent progression:

| District | Visual treatment |
| --- | --- |
| Brackenhaven | A sheltered reed-port with a survey office, tide board, and small observatory |
| Lockmere | Floodgates and abandoned canals marked with old measuring stones |
| Seedvault | A glass-and-wood greenhouse where light is redirected through prisms |
| Kitewatch | Wind shelves, signal flags, and high relay beacons |
| Coilmarket | A crowded tram market powered by a repaired relay coil |
| Stillbrine | A salt archive of flood records and dim, phosphorescent pools |
| Kilnreach | Ceramic conduits, cooling channels, and heat-warped instruments |
| Whitecap | A high spillway with ice, aurora-like resonance, and route markers |
| Crown Estuary | A paired-gate observatory where the region's tide cycle is visible |

Environmental puzzles should teach the player how people read and work with the landscape. They should not require unexplained machinery or turn every route into a laboratory.

## Pokémon identity and research

- Pokémon remain ordinary inhabitants and partners of this world. The research apparatus documents their behavior; it does not replace the familiar capture, training, evolution, and battle loop.
- The regional Pokédex contains 60 original species. Each species has one predetermined Delta form, for 60 standard species and 60 experimental forms.
- A completed, species-specific experiment permanently transforms the selected Pokémon; it does not create a duplicate. Explain that consequence before confirmation.
- Field Notes make discovery visible: where a species is found, what conditions draw it out, and what the player's observations have established.
- Research paths use a species-specific mix of encounter, observation, and practical field tasks. Rewards can include a signature move, ability, or another species-specific benefit.
- Delta forms change anatomy and sprite silhouette as well as typing; a palette swap alone is not a finished form.

## Interface direction

The existing purple Pokédex and Field Notes prototypes are a useful base. Evolve them into a survey instrument rather than a generic phone:

1. A compact species index with a strong silhouette, number, type marks, and clear discovery state.
2. A Field Notes page with encounter conditions and observation milestones.
3. A Research page showing what evidence is still missing and what a completed study unlocks.
4. A Delta page that explains the experiment and its permanent consequence before the player commits.

Use a dark blue-violet field, parchment record panels, teal status marks, and a limited cyan glow. Keep navigation and status legible on original GBA hardware. Avoid putting essential text in tiny ornamental labels.

## First visual vertical slice

Rework only the opening stretch before expanding the art workload:

- Title screen and opening scene establish the watershed, relay network, and surveyor role.
- Brackenhaven's palette, sign, lab/interior, and overworld landmarks establish the visual language.
- The starter selection and first route demonstrate that Pokémon sprites still read clearly against the new setting.
- One complete species Field Notes / Research / Delta flow demonstrates the science-fantasy interface and permanent-transformation rule.
- Lockmere's first gym puzzle turns the region's flood-control technology into an understandable Pokémon-style route challenge.

## Current implementation

The public `WiserOsprey/test` repository supplies the clean Pokémon Emerald (U) base ROM. The `WiserOsprey/airomhacktests` source branch has a reproducible GitHub Actions prototype build that checks that base against its expected SHA-1, applies the Reedwake opening and Bulbasaur interface patches, uses a matching pokeemerald source revision, installs the science-fantasy palette, and compiles a BPS patch.

That prototype is a buildable opening slice, not the complete regional game. The campaign conversion, all 60 regional species, their 60 Delta forms, the full sprite roster, and all routes and trainer data still need implementation.

The current early custom sprite files are prototypes. Some retain the source species' original silhouette with a new palette. They are below the intended art bar. Final standard and Delta sprites should be drawn as species-specific pixel art at the configured Emerald sprite dimensions, with clean silhouettes, coherent front/back anatomy, deliberate shade ramps, and readable details at native GBA scale. Do not ship the generated concept sheet directly as game art.

The science-fantasy palette is a six-bank JASC palette conversion used by the prototype build. The 240 × 160 Field Notes SVG remains a visual mockup/reference, not a complete in-game interface.
