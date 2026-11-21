# Purple Pokédex GBA background

This is a 240 × 160 conversion of the purple background-only image. It uses the same GBA text-background format and six 16-color palette banks as Emerald's Pokédex. The banks are fitted to the purple image. Color index 0 is reserved in every bank.

| File | Format |
| --- | --- |
| `background.4bpp` | 477 tiles of 8 × 8 pixels, 32 bytes per tile, including blank tile 0 |
| `list_underlay.bin` | 32 × 20 little-endian screen entries, matching the dimensions of Emerald's source underlay |
| `background.tilemap` | 32 × 32 screen entries with blank padding for a full 2 KiB GBA screenblock |
| `bg_national.pal` | JASC-PAL text with 96 entries, in six consecutive banks |
| `background.gbapal` | The same palette as 96 little-endian GBA RGB555 words |
| `preview.png` | 240 × 160 image decoded from the exported binaries |
| `emulator.png` | mGBA capture of the assets loaded into the Pokédex background |

Screen entries use bits 0–9 for the tile index, 10–11 for horizontal and vertical flips, and 12–15 for the palette bank. The visible area is 30 × 20 tiles. Each 4bpp byte packs the left pixel in its low nibble and the right pixel in its high nibble.

The artwork is packed into one opaque BG3 layer. Emerald's original list screen uses several layers for its overlay, window, and interface. To use the complete background, load the raw tiles into a free 16 KiB character block with tile base 0, copy the screenblock to BG3's configured map block, and load palette banks 0–5. In the Pokédex list loader, the original compressed graphics call uses a 0x2000-byte asset. This export is 0x3BA0 bytes and the verified capture loaded it uncompressed with `LoadBgTiles` using the actual file size. Disable the original list overlay for a background-only display. A functional reskin would also need matching foreground assets and palette handling.

The source was resized and quantized to the GBA resolution and color depth. The emulator capture matched the decoded preview at RGB555 precision.
