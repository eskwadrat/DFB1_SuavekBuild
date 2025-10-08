## David's Falcon Booster (DFB) with Suavek Build update - described down below in Suavek UPDATE section. 

#### An attempt to build a low-cost memory expansion and accelerator board for the Atari Falcon.

The primary goals of the project are to:

* Be a plug-in board requiring no soldering on the Falcon;
* Increase available RAM beyond the 14MB the stock Falcon can be expanded to;
* Be low cost;
* Provide some acceleration;
* Allow the PSU to remain in the case;
* Be open source.

Some development narration on this project is provided in the [Wiki](https://github.com/dh219/DFB/wiki).

Firmware source (ISE), board design files (KiCAD) and any source for support programs are published at each release.

#### Capabilities

As of 2024 the published firmware supports 64 (2x32) or 128 (2x64) MB of TT-RAM.

It supports only a PGA128 MC68030. The board has been tested between 32 and 50MHz with the CPU normally being the limiting factor.

The FPU is optional and can be run at half the CPU speed, or with an independent oscillator. This is configured by a resistor placement choice.

The Falcon's on-board FPU, if fitted, should be removed to prevent bus conflicts.

---

*Copyright 2020-24 D Henderson, released under GPL2.0*

#### Suavek UPDATE 

This is David Henderson Falcon accelerator design for Atari Falcon 030. 
Original design Github repository link: https://github.com/dh219/DFB

This fork contains David’s KiCad files for the PCB design, in which I slightly modified the silkscreen layer to make selected reference designators visible outside the component footprints. This ensures that when the board is assembled, the markings remain clearly visible.

Additional silkscreen cleanup involved removing silkscreen covering certain through-hole pads. I have no idea how these ended up there. Normally, such markings are flagged and removed by a CAM engineer at the PCB shop during fabrication if present, but I decided to correct them directly in the source file to avoid the risk of them being left in place. If manufactured that way, the silkscreen paint could cover plated-through holes, rendering the board unusable for assembly.

No other design changes were made to the original DFB1 board. There were no copper or component modifications of any kind.

The fork also includes a CPLD modification I introduced and tested to enable “dual boot” functionality for the DFB1’s on-board Flash.
Boot selection is controlled using the OPTION1 section of the J2 jumper. When the jumper is closed, the computer boots from Flash Bank 0 (A19 = 0); when open, it boots from Bank 1 (A19 = 1).
This mod is achieved by patching the original Verilog code for the CPLD, where I repurposed the OPTION1 jumper from its original RAM-size selection function to serve the new dual-boot feature. Since my DFB1 build is equipped with 64 MB of physical RAM, the jumper setting is no longer needed to select memory size as it would not change the installed RAM on the PCB. Therefore, we lose no functionality by repurposing the Option1 jumper and instead gain a useful new feature.

Steve Suavek, 10/08/2025
______________
