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
- Field Notes make discovery visible: where a species is found, what conditions draw it out, and what the player's observations have established.
- Preserve the earlier Delta design decisions if the 386-species scope remains active: one predetermined Delta form per species; a completed, species-specific experiment permanently transforms that Pokémon; and evolved forms may have separate, harder encounter paths.
- Research rewards can include a signature move, ability, or other species-specific benefit. The path should use a varied mix of encounter, observation, and practical field tasks, rather than a generic checklist repeated for every species.
- Keep prototype/sample content labeled as such until the complete roster and encounter plan are in the project.

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

## Implementation notes

The test repository currently contains the Reedwake campaign document, a starter/opening source patch, Emerald graphics reference material, a Pokédex background export, and a Bulbasaur research/Delta UI prototype. It does not contain a complete checked-out pokeemerald-expansion source tree. Treat binary/patch experiments as the current implementation boundary; do not claim the full campaign, all 386 Delta forms, or a distributable ROM is complete until those assets and systems are actually built and checked in.

The existing campaign document describes 60 original species. That is a separate roster decision from the earlier 386-species Delta plan and should not be silently treated as the same scope. Keep both documented until the project owner resolves how those plans fit together.
