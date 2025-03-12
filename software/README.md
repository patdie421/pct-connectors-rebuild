To use the PCT in good conditions it is preferable to have a ProDos hard drive. This disk can be a real disk connected to the II+/IIe/IIgs by one or other of the original solutions (SCSI card + HDD, Apple Profile, etc.) or a modern solution (SmartPort Emulator). However, not all solutions are compatible (I have already identified a solution that did not work), do your own tests if necessary.  

minimum storage device requirements to start MS-DOS with PCT :
- 1x 140ko floppy drive (real or emulated)

minimal usable configuration :
- 1x ProDOS bootable floppy drive (5.25" floppy drive is OK)
- 1x Apple 3.5" floppy drive plugged to DB19 connector at the back of the PCT

Optimal solution :
- 1x ProDOS bootable floppy drive (5.25" floppy drive is OK)
- 1x Apple 3.5" floppy drive (/!\ not Unidisk 3.5") plugged to DB19 connector at the back of the PCT
- 1x Real or emulated hard drive (>10 Go)

Top solution :
- 1x ProDOS bootable floppy drive (5.25" floppy drive is OK)
- 1x Transdrive (1x or 2x 5.25") plugged to DB19 connector at the back of the PCT
- 1x Apple 3.5" floppy drive plugged to DB19 connector at the back of the Transdrive
- 1x real or emulated hard drive (32 Go or 2x32 Go)

# Prebuild disk images

**pc_transporter_13_disks.zip** (1.32) and **pc_transporter_20_disk.zip** (2.04): original software for PCT Card  

**AEPCHD.2img**: hard drive disk image with PCT software (no dos hdd)  

**PCT204-msdos401us-v0.disk**: Apple II hard drive disk image with PCT 2.04 configured with:  
- A: apple drive 3.5",  
- C: 20MB Hard drive with MS-DOS 4.01 US (full install), no other software installed
- D: PCT Drivers and tools
(tested with Apple SCSI Card + BlueScsi and LIRON Card + floppy Emu)

**VOL01_HDD01.po**: hard drive disk image with PCT 2.04 configured with:  
- A: transdrive 5.25" (drive 1),
- B: apple drive 3.5" (drive 1),
- C: 30MB Hard drive with MS-DOS 4.01 US (full install) with software :
  - Turbo C++ 1.0
  - Turbo Pascal 5.5
  - Wordstar 4
  - Norton 5
- D: PCT Drivers and tools
(tested with DAN ][ - [https://github.com/profdc9/Apple2Card](https://github.com/thorstenBr/Apple2Card))  

(coming soon) **PCT140A2E.po** and **PCT140MSDOS33.po**: floppy disk image to boot PCT with only Apple II floppy drive / floppy Emu.  

PCT software does not seem to work with A2Pico + a2retronet (https://github.com/oliverschmidt/a2retronet)
