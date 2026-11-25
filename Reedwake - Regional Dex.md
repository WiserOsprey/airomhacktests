# Reedwake Regional Dex — 60 Species

This is the roster baseline for the full Reedwake campaign. It contains exactly 60 original regional species. Each species has one predetermined Delta form, unlocked through its own research experiment; completing the experiment permanently transforms that individual Pokémon. The existing prototype's six early replacements are temporary slot mappings and do not set the finished art or data quality bar.

## Roster structure

- 3 starter families (9 species)
- 8 gym-ace families (24 species)
- 9 additional wild families (27 species)
- Total: 20 families, 60 standard species plus 60 predetermined Delta forms

Gym aces remain the listed final stages and retain their campaign ace levels. Evolution levels are first-pass balance targets, selected so each ace stage can appear at its campaign level. Delta typing is one specific form per species, not a randomized choice.

| Family | Stage I | Stage II | Stage III / role | Standard typing | Delta typing by stage, I → II → III | Evolution targets | Ecological identity |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Fernut | Bramblet | Canoplate (starter) | Grass → Grass → Grass/Rock | Grass/Electric → Grass/Electric → Rock/Electric | 16, 36 | Rain-storing seed-shell gecko; its crown frond becomes a stone-braced canopy |
| 2 | Cindrix | Flareden | Vulprism (starter) | Fire → Fire → Fire/Dark | Fire/Ghost → Fire/Ghost → Dark/Psychic | 16, 36 | Ember fox-bird whose flame crest develops into a prism lens |
| 3 | Rillfin | Bendruff | Estuarch (starter) | Water → Water → Water/Fighting | Water/Ice → Water/Ice → Fighting/Ice | 16, 36 | River pup with a paddle tail; its final form braces against estuary currents |
| 4 | Peathare | Bogrel | Mirehart | Grass → Grass/Ground → Grass/Ground | Grass/Poison → Ground/Poison → Grass/Ghost | 16, 34 | A peatland hare that senses vibration through rootlike whiskers |
| 5 | Siltstilt | Reedrake | Fenstilt | Normal/Flying → Flying → Water/Flying | Normal/Steel → Flying/Steel → Water/Steel | 16, 34 | Wading marsh mammal-bird; long legs and silt-mask markings define its silhouette |
| 6 | Podtick | Silkettle | Latchwing | Bug → Bug → Bug/Steel | Bug/Fire → Bug/Fire → Bug/Fire | 7, 10 | Seed-pod larva that spins a ceramic-like cocoon and emerges with clasped metal wings |
| 7 | Siltmole | Gategrub | Lockmole (Gym 1 ace) | Ground → Ground/Rock → Ground/Steel | Ground/Water → Rock/Water → Steel/Water | 12, 14 | A floodgate burrower whose plated head opens and closes channels |
| 8 | Sporelet | Budwing | Graftwing (Gym 2 ace) | Bug → Bug/Grass → Bug/Grass | Bug/Poison → Grass/Poison → Bug/Poison | 10, 18 | Greenhouse pollinator that grafts living stems into protective wing veins |
| 9 | Gullit | Vaneagle | Galegull (Gym 3 ace) | Flying → Flying → Flying/Water | Flying/Electric → Flying/Electric → Water/Electric | 16, 26 | A ridge glider that reads wind shifts through split tail feathers |
| 10 | Tramkit | Voltrack | Arcrail (Gym 4 ace) | Electric → Electric → Electric/Steel | Electric/Ghost → Electric/Ghost → Steel/Ghost | 16, 30 | A curious rail-yard mammal that stores charge in conductive whisker bands |
| 11 | Saltmote | Brinewisp | Wakewisp (Gym 5 ace) | Ghost → Ghost → Ghost/Water | Ghost/Grass → Ghost/Ice → Ghost/Ice | 16, 38 | A drowned lantern phenomenon that gathers around recorded flood marks |
| 12 | Kilnlet | Potline | Glazeback (Gym 6 ace) | Fire → Fire/Rock → Fire/Rock | Fire/Water → Rock/Water → Fire/Water | 16, 42 | A kiln lizard whose shell vitrifies in cooling channels |
| 13 | Snowcap | Hushice | Calverime (Gym 7 ace) | Ice → Ice → Ice/Water | Ice/Electric → Ice/Electric → Water/Electric | 16, 46 | A spillway grazer that leaves branching frost patterns over stone |
| 14 | Gatecrab | Tideguard | Tiderook (Gym 8 ace) | Water → Water/Rock → Water/Steel | Water/Ground → Water/Ground → Steel/Ground | 16, 52 | A gate-building crustacean that locks itself against rising tides |
| 15 | Dewegg | Bellfrog | Fenchorus | Water → Water/Poison → Water/Poison | Water/Grass → Water/Grass → Poison/Grass | 16, 34 | A marsh amphibian whose throat sac resonates like a survey bell |
| 16 | Sootwing | Wickmoth | Lanterfly | Bug → Bug/Fire → Bug/Fire | Bug/Water → Bug/Water → Fire/Water | 10, 24 | A night pollinator that uses heat to reveal nectar-bearing plants |
| 17 | Draftlet | Shelfkite | Thermwing | Flying → Flying/Psychic → Flying/Psychic | Flying/Ice → Flying/Ice → Psychic/Ice | 16, 34 | A wind-shelf glider that senses pressure fronts before storms |
| 18 | Flintlet | Chertshell | Prismare | Rock → Rock → Rock/Psychic | Rock/Steel → Rock/Steel → Psychic/Steel | 16, 34 | A fossil-shell species that bends light through mineral growth rings |
| 19 | Coilfin | Sparkspine | Lumenstur | Water → Water/Electric → Water/Electric | Water/Psychic → Water/Psychic → Electric/Psychic | 16, 34 | A deep-channel fish that maps relay currents with electroreception |
| 20 | Rootling | Vineram | Wellwyrm | Grass → Grass/Ground → Grass/Dragon | Grass/Ice → Ground/Ice → Dragon/Ice | 16, 40 | A rare watershed guardian tied to the oldest headwater springs |

## Research and Delta rules

- Each species has a species-specific research path with a deliberate mix of encounter, observation, and practical battle or field tasks.
- Completing the research study unlocks a species-specific reward such as a signature move, ability, or other benefit.
- A Delta experiment reveals the one predetermined Delta typing and appearance for that species.
- The experiment permanently transforms the selected Pokémon; it does not create a second copy. Explain this consequence clearly before confirmation.
- Delta forms should have deliberate learnset, ability, and stat changes that fit the species' new ecology. Do not use a type-only recolor as a finished Delta design.

## Sprite craft requirements

The six current early forms are only an art prototype and do not set the finished quality bar. All 60 standard species and all 60 Delta forms need species-specific front and back battle sprites, icons, normal/shiny palettes, and overworld representations where the engine uses them. Evolved forms need new silhouettes and anatomy, not a larger recolor of the previous stage; Delta art also needs a distinct transformed silhouette or clear structural details.

For battle sprites, use the original Emerald asset conventions: transparent canvas at the species' configured dimensions (normally up to 64 × 64), crisp pixel clusters, readable silhouette at native size, selective dark outlines, consistent light direction, controlled edge highlights, and several intentional shade steps for each material. Keep palettes within the original GBA limits and reserve transparent index 0. Do not fill palette slots with black when sprite pixels can reference them. Front/back proportions should depict the same anatomy from different angles. Animation frames should preserve silhouette and palette consistency.

Generated concept images may guide shape and color, but they are not game assets. Redraw each sprite at native size, export indexed PNGs, and inspect in the emulator before it goes into a patch.

## Build milestones

1. **Opening art pass:** replace the six prototype starter/route species sprites with detailed, coherent front/back/icon art and proper palettes; create first evolutions so no early encounter evolves into a legacy species.
2. **Full regional dex:** implement all 60 species, their evolution stages and data, plus all 60 Delta transformations, research paths, Pokédex entries, abilities, learnsets, battle sprites, icons, and overworld sprites.
3. **Campaign conversion:** replace route layouts, scripts, encounters, trainers, gifts, and postgame content throughout the eight-gym campaign; retain Pokémon capture, evolution, training, and battle play.
4. **Verification:** build against the exact supplied Emerald base, test representative sprites, research paths, and encounters in mGBA, then produce a BPS patch only.

## Naming note

Names in this roster are working names. The first pass preserves the established names Fernut, Bramblet, Canoplate, Cindrix, Flareden, Vulprism, Rillfin, Bendruff, Estuarch, Peathare, Siltstilt, Podtick, Lockmole, Graftwing, Galegull, Arcrail, Wakewisp, Glazeback, Calverime, and Tiderook. All other names are provisional. Keep species names within the GBA's ten-character name limit; do not reuse existing Pokémon names or leave temporary base-species names in visible text.
