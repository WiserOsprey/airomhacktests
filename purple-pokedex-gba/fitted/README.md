# Fitted purple Pokédex foreground

The new overlay supplies a compact title, a pink selected-row pill, and a violet scroll track. The game still draws the entry names, counters, button labels, and creature sprites. The source patch clips the scrolling names to the right panel, scales the selected sprite to fit the left panel, and aligns the scroll controls to the track.

For the Emerald decompilation used by Reedwake, apply `pokedex-foreground.patch` at the source root. Copy the following files into `graphics/pokedex/purple/`.

- From this folder, copy `foreground.4bpp`, `foreground.tilemap`, and `foreground.gbapal`.
- From the parent folder, copy `background.4bpp`, `list_underlay.bin`, and `background.gbapal`.

Build normally and open the Pokédex in game. The foreground is 25 4bpp tiles starting at tile 733 and uses palette bank 12. The purple background uses tiles 256–732 and palette banks 6–11. The source patch styles the list and search-results list loader. Entry detail, area, and cry screens use separate loaders.

The included mGBA captures show the completed National list before and after scrolling down one entry. The temporary capture bootstrap that filled the Pokédex and opened it at startup is outside the patch.
