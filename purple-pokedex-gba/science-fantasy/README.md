# Science-fantasy Pokédex palette

This is a six-bank JASC-PAL variant for the existing 240 × 160 Pokédex background export. It keeps the original palette-bank structure and entry positions, shifts the dark field toward river indigo and teal, and moves the record panels toward parchment, bracken, and restrained resonance cyan. Entry 0 remains reserved in every bank.

The palette is an asset experiment, not a compiled ROM patch. Use it with the matching `background.4bpp` and `background.tilemap` from the parent directory, then rebuild the GBA palette binary and load it in the screen implementation. The screen still needs its foreground text, sprites, and menu states to be a complete in-game interface.
