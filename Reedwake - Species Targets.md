# Draft implementation targets: 60 regional species

These values are first-pass balancing data, not final tuning. Regional Dex numbers 001–060 follow family order. Stats are HP, Attack, Defense, Speed, Sp. Atk, Sp. Def. Delta forms keep the species' BST initially; their ability and type change are specified here, with battle testing still required.

| Dex | Family | Species | Stage | Type | Delta type | HP | Atk | Def | Spe | SpA | SpD | Ability | Delta ability | Evolves at | Evolves to |
| ---: | --- | --- | --- | --- | --- | ---: | ---: | ---: | ---: | ---: | ---: | --- | --- | ---: | --- |
| 001 | Fernut | Fernut | 1 | Grass | Grass/Electric | 45 | 45 | 55 | 45 | 50 | 50 | Overgrow | Static | 16 | Bramblet |
| 002 | Fernut | Bramblet | 2 | Grass | Grass/Electric | 60 | 60 | 70 | 60 | 65 | 65 | Chlorophyll | Static | 36 | Canoplate |
| 003 | Fernut | Canoplate | 3 | Grass/Rock | Rock/Electric | 80 | 90 | 95 | 65 | 95 | 85 | Rock Head | Lightning Rod |  |  |
| 004 | Cindrix | Cindrix | 1 | Fire | Fire/Ghost | 39 | 52 | 42 | 67 | 60 | 42 | Blaze | Levitate | 16 | Flareden |
| 005 | Cindrix | Flareden | 2 | Fire | Fire/Ghost | 58 | 73 | 55 | 84 | 80 | 56 | Flame Body | Levitate | 36 | Vulprism |
| 006 | Cindrix | Vulprism | 3 | Fire/Dark | Dark/Psychic | 78 | 95 | 72 | 110 | 118 | 82 | Flash Fire | Levitate |  |  |
| 007 | Rillfin | Rillfin | 1 | Water | Water/Ice | 50 | 55 | 55 | 55 | 45 | 55 | Torrent | Water Absorb | 16 | Bendruff |
| 008 | Rillfin | Bendruff | 2 | Water | Water/Ice | 65 | 75 | 75 | 65 | 60 | 70 | Swift Swim | Thick Fat | 36 | Estuarch |
| 009 | Rillfin | Estuarch | 3 | Water/Fighting | Fighting/Ice | 90 | 115 | 90 | 70 | 95 | 100 | Guts | Thick Fat |  |  |
| 010 | Peathare | Peathare | 1 | Grass | Grass/Poison | 50 | 45 | 50 | 55 | 40 | 45 | Run Away | Effect Spore | 16 | Bogrel |
| 011 | Peathare | Bogrel | 2 | Grass/Ground | Ground/Poison | 70 | 60 | 70 | 60 | 50 | 60 | Damp | Effect Spore | 34 | Mirehart |
| 012 | Peathare | Mirehart | 3 | Grass/Ground | Grass/Ghost | 95 | 80 | 90 | 55 | 65 | 100 | Natural Cure | Effect Spore |  |  |
| 013 | Siltstilt | Siltstilt | 1 | Normal/Flying | Normal/Steel | 40 | 50 | 40 | 70 | 35 | 45 | Keen Eye | Water Veil | 16 | Reedrake |
| 014 | Siltstilt | Reedrake | 2 | Flying | Flying/Steel | 65 | 75 | 55 | 90 | 50 | 60 | Early Bird | Water Veil | 34 | Fenstilt |
| 015 | Siltstilt | Fenstilt | 3 | Water/Flying | Water/Steel | 85 | 95 | 80 | 105 | 65 | 85 | Swift Swim | Lightning Rod |  |  |
| 016 | Podtick | Podtick | 1 | Bug | Bug/Fire | 45 | 50 | 40 | 35 | 25 | 30 | Shield Dust | Flame Body | 7 | Silkettle |
| 017 | Podtick | Silkettle | 2 | Bug | Bug/Fire | 55 | 55 | 85 | 15 | 45 | 70 | Shed Skin | Flame Body | 10 | Latchwing |
| 018 | Podtick | Latchwing | 3 | Bug/Steel | Bug/Fire | 65 | 105 | 95 | 75 | 55 | 90 | Sturdy | Flame Body |  |  |
| 019 | Lockmole | Siltmole | 1 | Ground | Ground/Water | 55 | 50 | 65 | 30 | 30 | 40 | Sand Veil | Water Absorb | 12 | Gategrub |
| 020 | Lockmole | Gategrub | 2 | Ground/Rock | Rock/Water | 70 | 70 | 95 | 35 | 40 | 60 | Sturdy | Water Absorb | 14 | Lockmole |
| 021 | Lockmole | Lockmole | 3 | Ground/Steel | Steel/Water | 90 | 105 | 125 | 45 | 55 | 90 | Sturdy | Water Absorb |  |  |
| 022 | Graftwing | Sporelet | 1 | Bug | Bug/Poison | 45 | 45 | 40 | 50 | 45 | 50 | Effect Spore | Poison Point | 10 | Budwing |
| 023 | Graftwing | Budwing | 2 | Bug/Grass | Grass/Poison | 55 | 60 | 55 | 75 | 65 | 65 | Chlorophyll | Poison Point | 18 | Graftwing |
| 024 | Graftwing | Graftwing | 3 | Bug/Grass | Bug/Poison | 75 | 90 | 75 | 90 | 100 | 85 | Swarm | Poison Point |  |  |
| 025 | Galegull | Gullit | 1 | Flying | Flying/Electric | 40 | 55 | 35 | 70 | 30 | 40 | Keen Eye | Static | 16 | Vaneagle |
| 026 | Galegull | Vaneagle | 2 | Flying | Flying/Electric | 60 | 80 | 55 | 95 | 45 | 55 | Guts | Static | 26 | Galegull |
| 027 | Galegull | Galegull | 3 | Flying/Water | Water/Electric | 85 | 100 | 75 | 125 | 75 | 85 | Swift Swim | Static |  |  |
| 028 | Arcrail | Tramkit | 1 | Electric | Electric/Ghost | 40 | 45 | 40 | 65 | 50 | 45 | Static | Levitate | 16 | Voltrack |
| 029 | Arcrail | Voltrack | 2 | Electric | Electric/Ghost | 60 | 65 | 55 | 95 | 75 | 65 | Static | Levitate | 30 | Arcrail |
| 030 | Arcrail | Arcrail | 3 | Electric/Steel | Steel/Ghost | 85 | 95 | 90 | 110 | 95 | 95 | Magnet Pull | Levitate |  |  |
| 031 | Wakewisp | Saltmote | 1 | Ghost | Ghost/Grass | 45 | 35 | 40 | 60 | 65 | 60 | Levitate | Natural Cure | 16 | Brinewisp |
| 032 | Wakewisp | Brinewisp | 2 | Ghost | Ghost/Ice | 60 | 45 | 55 | 75 | 90 | 80 | Water Absorb | Thick Fat | 38 | Wakewisp |
| 033 | Wakewisp | Wakewisp | 3 | Ghost/Water | Ghost/Ice | 80 | 70 | 80 | 95 | 115 | 105 | Intimidate | Thick Fat |  |  |
| 034 | Glazeback | Kilnlet | 1 | Fire | Fire/Water | 50 | 60 | 50 | 45 | 45 | 40 | Flame Body | Water Absorb | 16 | Potline |
| 035 | Glazeback | Potline | 2 | Fire/Rock | Rock/Water | 70 | 80 | 75 | 50 | 65 | 55 | Rock Head | Water Absorb | 42 | Glazeback |
| 036 | Glazeback | Glazeback | 3 | Fire/Rock | Fire/Water | 90 | 115 | 110 | 45 | 85 | 75 | White Smoke | Water Absorb |  |  |
| 037 | Calverime | Snowcap | 1 | Ice | Ice/Electric | 50 | 40 | 55 | 45 | 55 | 55 | Thick Fat | Static | 16 | Hushice |
| 038 | Calverime | Hushice | 2 | Ice | Ice/Electric | 65 | 55 | 75 | 55 | 80 | 75 | Inner Focus | Static | 46 | Calverime |
| 039 | Calverime | Calverime | 3 | Ice/Water | Water/Electric | 90 | 75 | 95 | 70 | 110 | 100 | Water Absorb | Static |  |  |
| 040 | Tiderook | Gatecrab | 1 | Water | Water/Ground | 50 | 65 | 65 | 30 | 35 | 45 | Shell Armor | Sand Veil | 16 | Tideguard |
| 041 | Tiderook | Tideguard | 2 | Water/Rock | Water/Ground | 70 | 85 | 90 | 40 | 55 | 65 | Battle Armor | Sand Veil | 52 | Tiderook |
| 042 | Tiderook | Tiderook | 3 | Water/Steel | Steel/Ground | 95 | 115 | 125 | 55 | 65 | 105 | Clear Body | Sand Veil |  |  |
| 043 | Fenchorus | Dewegg | 1 | Water | Water/Grass | 45 | 40 | 50 | 35 | 50 | 55 | Water Absorb | Chlorophyll | 16 | Bellfrog |
| 044 | Fenchorus | Bellfrog | 2 | Water/Poison | Water/Grass | 65 | 50 | 70 | 40 | 80 | 75 | Damp | Chlorophyll | 34 | Fenchorus |
| 045 | Fenchorus | Fenchorus | 3 | Water/Poison | Poison/Grass | 85 | 65 | 95 | 55 | 105 | 105 | Poison Point | Chlorophyll |  |  |
| 046 | Lanterfly | Sootwing | 1 | Bug | Bug/Water | 45 | 45 | 35 | 60 | 50 | 45 | Flame Body | Swift Swim | 10 | Wickmoth |
| 047 | Lanterfly | Wickmoth | 2 | Bug/Fire | Bug/Water | 60 | 55 | 50 | 80 | 75 | 65 | Swarm | Swift Swim | 24 | Lanterfly |
| 048 | Lanterfly | Lanterfly | 3 | Bug/Fire | Fire/Water | 75 | 70 | 65 | 115 | 100 | 90 | Flame Body | Swift Swim |  |  |
| 049 | Thermwing | Draftlet | 1 | Flying | Flying/Ice | 45 | 35 | 45 | 65 | 50 | 60 | Early Bird | Inner Focus | 16 | Shelfkite |
| 050 | Thermwing | Shelfkite | 2 | Flying/Psychic | Flying/Ice | 60 | 50 | 60 | 85 | 75 | 80 | Keen Eye | Inner Focus | 34 | Thermwing |
| 051 | Thermwing | Thermwing | 3 | Flying/Psychic | Psychic/Ice | 80 | 65 | 75 | 110 | 105 | 105 | Synchronize | Inner Focus |  |  |
| 052 | Prismare | Flintlet | 1 | Rock | Rock/Steel | 45 | 50 | 70 | 25 | 30 | 40 | Sturdy | Magnet Pull | 16 | Chertshell |
| 053 | Prismare | Chertshell | 2 | Rock | Rock/Steel | 65 | 65 | 100 | 30 | 45 | 65 | Rock Head | Magnet Pull | 34 | Prismare |
| 054 | Prismare | Prismare | 3 | Rock/Psychic | Psychic/Steel | 80 | 85 | 110 | 65 | 120 | 105 | Clear Body | Magnet Pull |  |  |
| 055 | Lumenstur | Coilfin | 1 | Water | Water/Psychic | 45 | 45 | 40 | 65 | 55 | 45 | Swift Swim | Synchronize | 16 | Sparkspine |
| 056 | Lumenstur | Sparkspine | 2 | Water/Electric | Water/Psychic | 65 | 60 | 55 | 85 | 80 | 65 | Lightning Rod | Synchronize | 34 | Lumenstur |
| 057 | Lumenstur | Lumenstur | 3 | Water/Electric | Electric/Psychic | 90 | 90 | 80 | 95 | 125 | 100 | Volt Absorb | Synchronize |  |  |
| 058 | Wellwyrm | Rootling | 1 | Grass | Grass/Ice | 50 | 50 | 55 | 45 | 55 | 50 | Natural Cure | Thick Fat | 16 | Vineram |
| 059 | Wellwyrm | Vineram | 2 | Grass/Ground | Ground/Ice | 75 | 80 | 80 | 55 | 75 | 70 | Rock Head | Thick Fat | 40 | Wellwyrm |
| 060 | Wellwyrm | Wellwyrm | 3 | Grass/Dragon | Dragon/Ice | 105 | 110 | 105 | 70 | 115 | 100 | Levitate | Thick Fat |  |  |

## Notes

This file contains first-pass stat and ability targets for implementation. Validate all ability identifiers against the chosen source revision; adjust level targets, stats, and encounter placement after trainer and route progression are in place. The listed ability is the standard form's initial ability; Delta uses the listed Delta ability. No custom abilities or moves are assumed in this first pass.
