# >**0x32**_ "Brussels Waffle". Lighter & Crispier. 
A 40% low-profile & wireless ortholinear board ⌨

> **Warning / Disclaimer**  
> These files are provided as a reference for designing keyboard PCBs, without liability and without any guarantees regarding functionality. 
> Although prototypes have been built and tested, errors may still be present.
> It is not advised to use them in your own project without electronics knowledge.


![0x32 Picture](./doc/0x32_pic01.jpg?raw=true "0x32 Picture")
More pictures: <https://imgur.com/a/yrJpx6d>

## Features

 * Powered by nRF52840 SoC
   * 32bit, 64MHz, 1Mo flash
   * Bluetooth 5.0
 * Advanced LiPo battery charging circuit (_see comments below_)
 * USB Type-C with ESD protection
 * Designed for Kailh PG1350 "Choc" switches
   * Uses the smaller choc 18×17mm pitch
   * Only 1u alphas & mods (+ 1.5 or 2u split spacebar)
 * Supports 1 centered (thumb) roller encoder 
 * Powered by ZMK

## Comments / Design discussion

The battery and power management circuitry was designed around the following ICs:

 * BQ24075 for LiPo charging
 * TPS63031 for (3.3V) voltage regulation

This can be considered as a relatively advanced design, in comparison with the "classical" TP4056 + DW01A + LDO combination, but is also far from perfect:

This was taken as a learning opportunity, and performance improvement (in terms of power efficiency), if any, has not been assessed, and is probably not worth the extra cost and design complexity.
This is especially true for the use of a Buck-Boost converter, as the gain in extra power recovery from the battery should be limited (to max 5% capacity wrt a simpler Buck, or even a good quality LDO linear regulator).

I would however always recommend the use of high-quality components when it comes to LiPo battery management...

Other design limitations:
 * The lack of a LED tied to an IO of the MCU module, making it impossible to (externally) identify when the device is in bootloader mode.
 * The two available LEDs are used for power management / battery charging are sandwiched between the PCB and the switch plate, thus not replaceable once the board is assembled.

No PCBA files are provided since the few proto boards were assembled by hand (human PnP and reflow oven).

## Battery

The cutout in the PCB has been designed to accomodate a **402535** LiPo battery (~300mAh), sandwiched between switch & bottom plates.

## Layout

![0x32 Layout](./doc/0x32_layout.png?raw=true "0x32 Layout")

## License

Copyright Charles Fourneau, 2021.

This source describes Open Hardware and is licensed under the _CERN-OHL-W_ v2

You may redistribute and modify this documentation and make products using it under the terms   of the CERN-OHL-W v2 (<https:/cern.ch/cern-ohl>). This documentation is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY, INCLUDING OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A PARTICULAR PURPOSE. Please see the CERN-OHL-W v2 for applicable conditions.

## Credits

0x32 is a new design but inspired by boards like:
 - Hadron by Ishtob
 - Boardwalk by AlexAtPanc, Shensmobile & others
 - Planck (Light) by OLKB
 - Pancake by Spaceman
 - ...some if my previous designs 😄

And special thanks to [ebastler](https://github.com/ebastler) for providing information I used as reference design for Holyiot modules.
