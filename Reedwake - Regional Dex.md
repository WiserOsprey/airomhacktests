# Reedwake Regional Dex — 60 Species

This is the roster baseline for the full Reedwake campaign. The scope is exactly 60 original regional species. The existing prototype swaps six early species into legacy Emerald species slots; the finished build will replace those temporary slot mappings with proper species definitions, complete evolution lines, and new sprites.

## Roster structure

- 3 starter families (9 species)
- 8 gym-ace families (24 species)
- 9 additional wild families (27 species)
- Total: 20 families, 60 species

Gym aces remain the listed final stages and retain their campaign ace levels. Evolution levels below are first-pass balance targets, selected so each ace stage can appear at its campaign level.

| Family | Stage I | Stage II | Stage III / role | Typing | Evolution targets | Ecological identity |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Fernut | Bramblet | Canoplate (starter) | Grass → Grass → Grass/Rock | 16, 36 | Rain-storing seed-shell gecko; its crown frond becomes a stone-braced canopy |
| 2 | Cindrix | Flareden | Vulprism (starter) | Fire → Fire → Fire/Dark | 16, 36 | Ember fox-bird whose flame crest develops into a prism lens |
| 3 | Rillfin | Bendruff | Estuarch (starter) | Water → Water → Water/Fighting | 16, 36 | River pup with a paddle tail; its final form braces against estuary currents |
| 4 | Peathare | Bogrel | Mirehart | Grass → Grass/Ground → Grass/Ground | 16, 34 | A peatland hare that senses vibration through rootlike whiskers |
| 5 | Siltstilt | Reedrake | Fenstilt | Normal/Flying → Flying → Water/Flying | 16, 34 | Wading marsh mammal-bird; long legs and silt-mask markings define its silhouette |
| 6 | Podtick | Silkettle | Latchwing | Bug → Bug → Bug/Steel | 7, 10 | Seed-pod larva that spins a ceramic-like cocoon and emerges with clasped metal wings |
| 7 | Siltmole | Gategrub | Lockmole (Gym 1 ace) | Ground → Ground/Rock → Ground/Steel | 12, 14 | A floodgate burrower whose plated head opens and closes channels |
| 8 | Sporelet | Budwing | Graftwing (Gym 2 ace) | Bug → Bug/Grass → Bug/Grass | 10, 18 | Greenhouse pollinator that grafts living stems into protective wing veins |
| 9 | Gullit | Vaneagle | Galegull (Gym 3 ace) | Flying → Flying → Flying/Water | 16, 26 | A ridge glider that reads wind shifts through split tail feathers |
| 10 | Tramkit | Voltrack | Arcrail (Gym 4 ace) | Electric → Electric → Electric/Steel | 16, 30 | A curious rail-yard mammal that stores charge in conductive whisker bands |
| 11 | Saltmote | Brinewisp | Wakewisp (Gym 5 ace) | Ghost → Ghost → Ghost/Water | 16, 38 | A drowned lantern phenomenon that gathers around recorded flood marks |
| 12 | Kilnlet | Potline | Glazeback (Gym 6 ace) | Fire → Fire/Rock → Fire/Rock | 16, 42 | A kiln lizard whose shell vitrifies in cooling channels |
| 13 | Snowcap | Hushice | Calverime (Gym 7 ace) | Ice → Ice → Ice/Water | 16, 46 | A spillway grazer that leaves branching frost patterns over stone |
| 14 | Gatecrab | Tideguard | Tiderook (Gym 8 ace) | Water → Water/Rock → Water/Steel | 16, 52 | A gate-building crustacean that locks itself against rising tides |
| 15 | Dewegg | Bellfrog | Fenchorus | Water → Water/Poison → Water/Poison | 16, 34 | A marsh amphibian whose throat sac resonates like a survey bell |
| 16 | Sootwing | Wickmoth | Lanterfly | Bug → Bug/Fire → Bug/Fire | 10, 24 | A night pollinator that uses heat to reveal nectar-bearing plants |
| 17 | Draftlet | Shelfkite | Thermwing | Flying → Flying/Psychic → Flying/Psychic | 16, 34 | A wind-shelf glider that senses pressure fronts before storms |
| 18 | Flintlet | Chertshell | Prismare | Rock → Rock → Rock/Psychic | 16, 34 | A fossil-shell species that bends light through mineral growth rings |
| 19 | Coilfin | Sparkspine | Lumensturgeon | Water → Water/Electric → Water/Electric | 16, 34 | A deep-channel fish that maps relay currents with electroreception |
| 20 | Rootling | Vineram | Wellwyrm | Grass → Grass/Ground → Grass/Dragon | 16, 40 | A rare watershed guardian tied to the oldest headwater springs |

## Sprite craft requirements

The six current early forms are only an art prototype and do not set the finished quality bar. Every regional species needs species-specific front and back battle sprites, icons, normal/shiny palettes, and an overworld representation where the engine uses one. Evolved forms need new silhouettes and anatomy, not a larger recolor of the previous stage.

For battle sprites, use the original Emerald asset conventions: transparent 64 × 64 canvas where applicable, crisp pixel clusters, readable silhouette at native size, selective dark outlines, consistent light direction, controlled edge highlights, and several intentional shade steps for each material. Keep palettes within the original GBA limits and reserve transparent index 0. Do not fill unused color slots with black if any sprite pixel can reference them. Front/back proportions should feel like the same creature from different angles. Animation frames should preserve silhouette and palette consistency.

Do not install generated concept images directly as game assets. Treat them as shape and color references; redraw and check each sprite at native 64 × 64 size, then export indexed PNGs and validate them in the emulator.

## Build milestones

1. **Opening art pass:** replace the six prototype starter/route species sprites with detailed, coherent front/back/icon art and proper palettes; create first evolutions so no early encounter evolves into a legacy species.
2. **Full regional dex:** implement all 60 species, all evolution stages, Pokédex entries, abilities, learnsets, battle sprites, icons, and overworld sprites.
3. **Campaign conversion:** replace route layouts, scripts, encounters, trainers, gifts, and postgame content throughout the eight-gym campaign; retain Pokémon capture, evolution, training, and battle play.
4. **Verification:** build against the exact supplied Emerald base, test representative sprites and encounters in mGBA, then produce a BPS patch only.

## Naming note

Names in this roster are working names. The first pass preserves the established names Fernut, Bramblet, Canoplate, Cindrix, Flareden, Vulprism, Rillfin, Bendruff, Estuarch, Peathare, Siltstilt, Podtick, Lockmole, Graftwing, Galegull, Arcrail, Wakewisp, Glazeback, Calverime, and Tiderook. All other names are provisional. The regional Dex should not reuse existing Pokémon names or leave temporary base-species names in visible text.
