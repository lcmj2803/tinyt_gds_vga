<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

`bitmap_rom` stores a 128 × 128 monochrome image in 2,048 bytes. The 7-bit inputs `x` and `y` select coordinates from 0 to 127; `pixel` outputs the stored bit at that position.

The byte address is `y * 16 + (x >> 3)`. The lower three bits of `x` select a bit within that byte, starting with the least significant bit. Reads are combinational, so this ROM needs no clock. A separate VGA module provides scanning coordinates and maps the pixel to a color.

## How to test

Simulate the ROM and apply these coordinates after initialization. For the supplied image data, the expected outputs are:

| x | y | pixel |
|---:|---:|---:|
| 0 | 0 | 0 |
| 7 | 0 | 1 |
| 8 | 0 | 1 |
| 127 | 127 | 0 |

For a visual test, connect the ROM to the VGA top module and confirm that the image appears within its 128 × 128 display region.

## External hardware

No external hardware is required for browser simulation. For a physical display, use a suitable FPGA or ASIC development board with VGA output circuitry, a VGA cable, and a compatible monitor or projector. The complete design also needs a pixel clock and VGA timing/RGB logic.

