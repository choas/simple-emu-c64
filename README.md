# simple-emu-c64 #
Here is a simple Commodore (64, PET 2001, VIC-20, Commodore 16, Plus/4, ...) and 6502 Emulator I wrote from scratch.  Runs in a text console window.

Notable features

* Emulates MOS6502
* Runs as a Windows Console Program (source is C#, also ported to C at [c-simple-emu6502-cbm](https://github.com/davervw/c-simple-emu6502-cbm))
* Text based Commodore BASIC and 6502 Assembly/Machine Code programs supported
* only a few hooks: CHRIN-$FFCF/CHROUT-$FFD2/COLOR-$D021/199/646 (COLOR background/inverse $9001 on VIC-20)
(also hooked READY, GETIN, STOP, SETLFS, SETNAM, LOAD, SAVE on C64 for better simulation)

![Sample.bas](https://github.com/davervw/simple-emu-c64/raw/master/Sample.png)

USAGE:

    simple-emu-c64
    simple-emu-c64 help
    simple-emu-c64 c64 ram 4
    simple-emu-c64 c64
    simple-emu-c64 c64 startup.prg
	simple-emu-c64 c64 walk
	simple-emu-c64 c64 walk FFD2
    simple-emu-c64 vic20
    simple-emu-c64 vic20 ram 7
    simple-emu-c64 vic20 ram 28
    simple-emu-c64 vic20 ram 39
    simple-emu-c64 vic20 walk
    simple-emu-c64 vic20 walk FFD2 FFCF
    simple-emu-c64 pet
    simple-emu-c64 pet ram 32
    simple-emu-c64 pet walk
    simple-emu-c64 c16
    simple-emu-c64 plus4
    simple-emu-c64 ted ram 32
    simple-emu-c64 ted walk

LIMITATIONS:

* Only keyboard/console I/O.  No text pokes, no graphics.  Just stdio.  Asynchronous input (GET K$) currently implemented for C64 only, but INPUT S$ works.  No special Commodore keys, e.g. function keys, cursor keys, color keys, STOP/RESTORE, etc.  ESC currently implemented as STOP for C64 only.
* No keyboard color switching.  No border or border color.
* No screen editing (gasp!) Just short and sweet for running Commodore BASIC in terminal/console window via 6502 chip emulation in software.  Uses Windows Console line editor features instead.
* No PETSCII graphic characters, only supports printables CHR$(32) to CHR$(126).  But does support CHR$(147) for clear screen and Home/Left/Right/Up/Down characters too (output only).
* C64 RAM/ROM/IO/CHARSET banking is implemented!
* Plus/4 implementation has banking enabled, can access almost 60K RAM for BASIC!
* VIC-20 memory is configurable, can access almost 28K RAM for BASIC!  Plus 11K more for machine code.
* No timers.  No interrupts except BRK.  No NMI or RESTORE key.
* Loading and saving of files currently implemented only for C64 (but Windows clipboard works!)
* Where do I plug in my cartridge?  What, no joystick?
* Lightly tested.  Bugs are lurking! 

CREDITS:

* [Micro Logic Corp. 6502 (65XX) Microprocessor Instant Reference Card](https://archive.org/details/6502MicroprocessorInstantReferenceCard)
* Compute's [Mapping the Commodore 64](https://archive.org/details/Compute_s_Mapping_the_Commodore_64)
* Compute's [Mapping the VIC](https://archive.org/details/COMPUTEs_Mapping_the_VIC_1984_COMPUTE_Publications)
* [VICE](https://vice-emu.sourceforge.io/) for performing trace comparisons 
* Commodore 64 and VIC-20 BASIC/KERNAL ROM from [VICE](https://vice-emu.sourceforge.io/) or [Zimmers.net](http://www.zimmers.net/anonftp/pub/cbm/firmware/computers/c64/) or other
* Inspired by [mist64/cbmbasic](https://github.com/mist64/cbmbasic)
* Built with Microsoft Visual Studio 2017, .NET Framework 4, C#

Read the blog Entry at [davevw.com](https://techwithdave.davevw.com/2020/03/simple-emu-c64.html)