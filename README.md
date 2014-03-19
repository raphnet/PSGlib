PSGlib
======

Z80 ASM library (and C conversion/compression tools) to allow replay of VGMs as background music/SFX in SEGA 8 bit homebrew programs

Typical workflow:

1) You (or a friend of yours) track one or more module(s) and SFX(s) using either Mod2PSG2 or DefleMask (or whatever you prefer as long as it supports exporting in VGM format).

2) Optional, but warmly suggested: optimize your VGM(s) using Maxim's VGMTool

3) Convert the VGM to PSG file(s) using the vgm2psg tool.

4) Optional, suggested: compress the PSG file(s) using the psgcomp tool. The psgdecomp tool can be used to verify that the compression was right.

5) include the library and 'incbin' the PSG file(s) to your Z80 ASM source.

6) call PSGInit once somewhere near the beginning of your code.

7) Set up a steady interrupt (vertical blanking for instance) so to call PSGFrame and PSGSFXFrame at a constant pace (very important!). The two calls are separated so you can eventually switch banks when done processing background music and need to process SFX.

8) Start/stop tunes when needed using PSGPlay and PSGStop calls, start/cancel SFXs when needed using PSGSFXPlay and PSGSFXStop calls. Looping SFXs are supported too, fire them using a PSGSFXPlayLoop call.
