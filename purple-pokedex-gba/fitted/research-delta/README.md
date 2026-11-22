# Bulbasaur Field Notes

Open Bulbasaur's Pokédex entry and press **L** or **R** to cycle through Encounter, Research, and Delta. The lock line shows question marks before an unlock. Completed steps use Safari Ball markers. Research and Delta keep the best completed step count, but their unlock conditions evaluate actions within a single battle.

## Research

Use Absorb, Growth, and Razor Leaf in that order with the same Bulbasaur in one regular battle. Bulbasaur learns these moves at levels 18, 19, and 20. The research reward is **Solar Leaf**, a 75-power Grass move with a high critical-hit rate, 100% accuracy, and 15 PP. It uses Razor Leaf's animation.

After unlocking the move, press **A** on the Research page to teach it to the first regular Bulbasaur in the party that can learn it. If its moveset is full, **Select** cycles the replacement slot, **A** confirms the replacement, and **B** cancels.

## Delta

Buy Toxic Sludge at the Oldale Mart. Give it to Bulbasaur, use a Poison-type move with that Bulbasaur in an underground battle, and win. The Delta page reveals the Poison-type form and displays its purple-and-lime sprite palette. Delta Bulbasaur has Poison Point and a Poison-type learnset.

Once unlocked, Delta Bulbasaur replaces the next eligible land encounter in an underground map and remains available until caught. Research and Delta progress is stored in the normal game save.

## Build and verification

The supplied GBA build boots into the game normally. A regular Bulbasaur must already be available to the player. The original Encounter page displays the berry checklist and has no encounter trigger in this build.

For source integration, start with the Reedwake source and the two fitted patches in the parent directory. Install their background and foreground assets as documented there. Apply `pokedex-foreground.patch`, then `bulbasaur-field-notes.patch`, then `research-delta.patch`. The last patch includes the Delta palettes.

The screenshots were captured in mGBA with a temporary fixture. The fixture exercised the battle tracking functions, including cross-battle and cross-party rejection, cave loss and win, and the caught state. Emulator input checks covered page navigation, the replacement prompt, cancellation, and teaching Solar Leaf. The normal ROM was smoke-tested through the New Game menu.
