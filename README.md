# pct-connectors-rebuild
This repository consolidate all the elements which allow to use an "AE PC Transporter" card in an Apple IIe or IIgs. In particular, It contains elements allowing to recreate the cables and connectors which are generally lost when one of these cards is found.  
Most of the data used to produce the resources of this repository comes from various sources available on the Internet and are referenced in the “useful links” section.  
Colorswitch PCB was created by retro-ingeniring and original card.

<div style="text-align:center;">

![figure 1: PC Transporter rev D](images/image.png)  
<p>figure 1: PC Transporter rev D (front view)</p>
</div>

## Connector locations  
### PCT Card
<div style="text-align:center;">

![figure 2: PC Transport connector location](images/IMG_3021.jpeg)
<p style="text-align:center;">figure 2: front view card diagram with connector locations</p>
<pre>
J1 - Apple II Speaker motherboard connector (INPUT)
J2 - Composite video (OUTPUT)
J3 - IIe keyboard adapter (INPUT)
J4 - PC Transporter Disk drive (INPUT/OUTPUT)
J5 - PC Compatible keyboard (XT protocol) (INPUT)
J6 - ColorSwitch/CGA (OUTPUT)
J7 - Apple II Speaker (OUTPUT)
</pre>
</div>

### Apple IIe
<div style="text-align:center;">

![figure 3: Apple IIe PAL motherboard](images/IMG_3023.jpeg)  
<p>figure 3: Apple IIe PAL motherboard</p>

![figure 4: Apple IIe (platinum) US motherboard](images/IMG_3042.jpeg)  
<p>figure 4: Apple IIe (platinum) US motherboard</p>
<pre>
J13 (A14)                  - Composite video (INPUT/OUPUT)
J17 (PAL:E/F15, US:B14)    - IIe keyboard adapter (INPUT)
PAL:J18 (F2), US:J10 (F14) - Apple II Speaker motherboard connector (OUTPUT)
</pre>
Note the different spacing between the keyboard connector (J17) and the numeric keypad connector (J16) of the two card versions.
</div>

## Video Composite output
Simple two wires cable. Cheap female/female jumper wire can be used.
PCT Card outputs an NTSC composite video signal on J2. PAL motherboards can nevertheless be wired to this Molex connector, but the monitor must be able to switch NTSC and PAL signals (Apple Monitor II is OK for that).
### Molex connector
<pre>
____
|2||   Video Composite (NTSC)
|1||   GND
----
(front view)
</pre>
### Apple II internal Video Connector (J13)
<pre>
===========
| 4 3 2 1 |
-----------
(Front view)

1  GND
2  Video Composite (NTSC or PAL)
3  -5V
4  +12V
</pre>

### Video Cable
<pre>
Molex  Apple II connector
1  -   1
2  -   2
   -   3
   -   4
</pre>

### status
done, working.

## CGA Video cable (AE Digital RGB Adapter)
<img src="images/IMG_3006.jpeg" width="800">

This cable is to use to output video signal directly to a CGA compatible monitor (TTL monitor). Apple II and PCT card can't share easily the same connection for this kind of video connection. Same monitor can display Apple II and PCT signal but for now through two different cables and adaptors (some monitor can automatically switch inputs and "emulate" composite switch or colorswitch behavior)

One side is a DB9 Male connector.
Other one a "10 pins male IDC connector".

Ribbon cable mount connectors are the best way to make this cable. Some parts that could be used :

- IDC : https://fr.farnell.com/en-FR/wurth-elektronik/61201025821/plug-idc-2-54mm-strain-relief/dp/2356318
- DB9 : https://fr.farnell.com/en-FR/multicomp-pro/8ftm09p-30n1-fec/plug-idc-d-threaded-9way/dp/1099306

### 10 pin IDC Male  
<img src="images/IMG_2977.jpeg" width="300">
<pre>
(front view)  
____________________   
| 2   4   6   8  10|  
| 1   3   5   7   9|  
--------|   |-------  
  |1             |  
  |ribbon  cables|  
  
1 GND
2 Intensity
3 NC for CGA - Source selection for Colorswitch (PCT output signal on CGA/Composite)
4 NC for CGA - CSync for Colorswitch
5 Red
6 HS for CGA - NC for Colorswitch
7 Green
8 VS for CGA - NC for Colorswitch
9 Bleu
10 -
</pre>

### DB9 Female
<img src="images/IMG_3007.jpeg" width="300">
(note the cutout in the ribbon cable)  
  
<pre>
 | ribbon  |
 | cables  |
_|_______ 1|_
\ 5 4 3 2 1 /
 \ 9 8 7 6 /
  ---------
(front view)

Pin  CGA Function
1    GND
2    GND
3    Red
4    Green
5    Blue
6    Intensity
7    Reserved
8    Horizontal Sync
9    Vertical Sync
</pre>

### Cable
<pre>
IDC      DB9  
  1  --  1  
  2  --  6  
  3  xx  2  
  4  xx  7  
  5  --  3  
  6  --  8  
  7  --  4  
  8  --  9  
  9  --  5  
  10  
</pre>
Do not connect 3 and 4 IDC pins. Cut strands 3 and 4 of the ribbon cable (see photo).  
### usage
The cable connects to J6. There is no key on the male connector, the cable "points" to the right (female connector notch on the right if you look at the board as it is shown in Figure 1). 
### Bonus
You can have cristal clear output on HDMI monitor by using RGBtoHDMI (https://github.com/hoglet67/RGBtoHDMI). The profile to use is : [Commodore/Commodore 128 CGA Brown]  
<img src="images/IMG_3022.jpeg" width="400">
### status
done, working.

## Colorswitch
The ColorSwitch was designed to allow a PCT-equipped Apple IIGS to display CGA on a standard A2M6014 monitor or a compatible RGB monitor (ex: Sony RGB Monitor, cf AE catalog). When the PCT software is running, the display automatically switches Apple screen to CGA screen.
This card can also be used with an Apple 2e using an RGB color card (Chat Mauve Féline in my case)  
<div>
<img src="images/IMG_3182.jpeg" width="300">
</div>
<div>
<img src="images/colorswitch_med.jpeg" width="300">
</div>

### PCB
A design is available in "hardware" folder (v0.0 is buggy, v0.2 should work).  
This design differs from the original device. The implementation density of components is reduced (easier to solder) and the faulty and unused/useless* composite video signal circuit has been removed.  
(*) would have been useful with a specific monitor able to display RGB and composite. Could be add in a futur version.   
<div>
   <p><img src="images/IMG_3200.jpeg" width="300"></p>
   Rebuilt Colorswitch (v0.0) with DB25 mounting bracket compared to original 
</div>

#### ColorSwitch DB15 female connector
<pre>
1 : RED GND
2 : RED
3 : CSYNC
4 : -
5 : GREEN
6 : GREEN GND
7 : -
8 : -
9 : BLUE
10 : -
11 : -
12 : -
13 : BLUE GND
14 : -
15 : -
</pre>

### ColorSwitch IDC6 connector
<pre>
1 : CSYNC
2 : (composite)
3 : GREEN
4 : RED
5 : BLUE
6 : GND
</pre>

### PCT to Colorswitch cable
flat cable with 2 idc10 male connector.  
<div>
   <p><img src="images/IMG_3227.jpeg" width="300"></p>
</div>
<pre>
IDC10  IDC10  
   1 -- 1
   2 -- 2
   3 -- 3
   4 -- 4
   5 -- 5
   6 -- 6
   7 -- 7
   8 -- 8
   9 -- 9
  10 -- 10
</pre>
flat cable with 2 idc10 male and 1 db9 male connector. To use for double monitor connection.  
(photo)
<pre>
IDC10  IDC10   DB9  
  1  --  1  --  1
  2  --  2  --  6
  3  --  3  xx  2
  4  --  4  xx  7
  5  --  5  --  3
  6  --  6  --  8
  7  --  7  --  4
  8  --  8  --  9
  9  --  9  --  5
  10 -- 10
</pre>

### db15 to Colorswitch cable (for Apple IIGS)

(to do)

### Chat Mauve to Colorswitch cable
Several connection are possible. You can use internal (on card) or external connector (throug db connectors).

#### Chat Mauve on card IDC8 connector
<pre>
  (card connector)  
  =================  
  |1 2 3 4 5 6 7 8|  
  -----------------  
1 - RGB/Composite commutation
2 - Audio out
3 - CSYNC (75 Ohms, 0.5V)
4 - RED (75 Ohms, 0 to 0.7V)
5 - GREEN (75 Ohms, 0 to 0.7V)
6 - BLUE (75 Ohms, 0 to 0.7V)
7 - GND
8 - 12V
</pre>
#### BONUS 1 : Chat Mauve Féline on card IDC10 connector (connector need to be soldered)
<pre>
  (card connector) 
  ---------------
  |2  4  6  8 10|
  |1  3  5  7  9|
  ---------------  
 1 - NC
 2 - 12v
 3 - GND
 4 - Blue
 5 - Green
 6 - Red
 7 - CSync
 8 - Audio
 9 - NC
10 - NC
</pre>
#### Chat Mauve DB9 female connector
<pre>
_____________  
\ 5 4 3 2 1 /  
 \ 9 8 7 6 /  
  ---------  
1 : NC  
2 : GND  
3 : GREEN (75 Ohms, 0 to 0.7V)  
4 : CSYNC (negative, 75 Ohms, 0.5V)  
5 : RGB/Composite commutation  
6 : 12V
7 : BLUE (75 Ohms, 0 to 0.7V)  
8 : RED (75 Ohms, 0 to 0.7V)  
9 : Audio out
</pre>

### BONUS 2 : Chat Mauve to A2M6014 compatible monitor
<pre>
DB9    DB15      IDC8    DB15     IDC10*  DB15
  1 --              1 --             1  --  
  2 -- 1,6,13       2 --             2  --  
  3 -- 5            3 -- 3           3  -- 1,6,13
  4 -- 3            4 -- 2           4  -- 9
  5 --              5 -- 5           5  -- 5
  6 --              6 -- 9           6  -- 2 
  7 -- 9            7 -- 1,6,13      7  -- 3
  8 -- 2            8 --             8  --  
  9 --                               9  --  
                                    10  --  
</pre>

### BONUS 3 : Colorswitch (or 2gs) to scart cable
#### Scart pinout (wire side view)
<pre>
  _____________________________
 |1  3  5  7  9 11 13 15 17 19 |
 | 2  4  6  8  10 12 14 16 18 20\
  -------------------------------
5  - RGB Ground Blue
7  - RGB Blue In
9  - RGB Ground Green
11 - RGB Green In
13 - RGB Ground Red
15 - RGB Red In 
16 - Blanking Signal  
17 - Ground Composite Video
18 - Ground Blanking Signal
20 - Composite Video In (CSYNC)
(Only needed pins are listed)
</pre>

#### cable
<pre>
   DB15 (male)   scart (male)
   1,6,13    --- 5,9,13,17,18
   2         --- 15
   3         -*- 20
   4
   5         --- 11
   7
   8         -o- 8
   9         --- 7
   10
   11
   12
   14
   15
(-*-) : direct wire or 190 Ohms resistor
(-o-) optional : to use the cable with the 2gs db15 connector add a 390 Ohms resistor
</pre>

### BONUS 4 : Chat Mauve TTL connector to rgbtohdmi
(to do)  

### Status
v0.0 : partially working, color inversion but pcb OK  
v0.2 : work in progress (pcb fabrication)  

## Storage connector  
<img src="images/IMG_2981.jpeg" height="200">

### 20 pin IDC Female  
<pre>
_________________________________________   
| 20  18  16  14  12  10  8   6   4   2 |  
| 19  17  15  13  11   9  7   5   3   1 |  
------------------|   |------------------  
  |                                  1|  
  |           ribbon cables           | 
(front view)  
</pre>
### DB19 Female
<pre>
  |                              |
 _|_____________________________1|_
 \  10  9  8  7  6  5  4  3  2  1 /
  \  19 18 17 16 15 14 13 12 11  / 
   ------------------------------  
(front view)

Pin Function apple pinout
1   GND      GND
2   GND      GND
3            GND
4            GND (IIgs: /3.5DISK bidirectional)
5            -12V
6   5V       +5V
7   12V      +12V
8   12V      +12V
9            /ENABLE2 (IIc /EXTINT)
10           WPROD (Macintosh: PWM)
11           PHASE0
12           PHASE1
13           PHASE2 
14           PHASE3
15           /WREQ
16           (Machintosh: SELECT, IIe/II+: +5V, IIc: N.C., IIgs: SELECT bidirectional)
17           /ENABLE (II+/IIe/IIgs: /ENABLE1)
18           RD
19           WR
</pre>

### Cable
<pre>
IDC    DB9  
1  --  1  
2  -- 11  
3      2  
4     12  
5  --  3  
6  -- 13  
7  --  4  
8  -- 14  
9  --  5  
10 -- 15
11 --  6
12 -- 16
13 --  7
14 -- 17
15 --  8
16 -- 18
17 --  9
18 -- 19
19 -- 10
20
</pre>
### usage
The IDC connector is keyed (the cable is oriented towards the inside of the apple II). Connect 800ko 3.5" Apple floppy drive (/!\ do not connect 3.5" unidisk) or AE Transdrive to DB19 connector. Drive can be daisy chained check documentation.

### status
done, working.

## Apple 2e keyboard adapter
<img src="images/IMG_3043.jpeg" width="400">
<img src="images/IMG_3044.jpeg" width="400">
The keyboard adapter is a small PCB and a ribbon cable supplied as an option with the PCT card. This adapter is placed between the Apple motherboard and the keyboard and provides status of "dead keyboard keys" (control, shift, Apple open/close and capslock) to the PCT card. The other signals are only pass-throughs from the keyboard to the motherboard of the Apple 2e.

### connections
Connections are described in this [schema](hardware/a2keyboardToPCT/a2keyboardToPCT.pdf)

### PCB
Based on the connections schema, it can be found in this repository:
[KiCad project and gerber files](hardware/a2keyboardToPCT/V0.0)  
The original version of the connector was designed for a US motherboard. It can be installed on a PAL computer but the connector for the numeric keypad may conflict with the keyboard adapter.  
This PCB is roughly the same size and layout as the original one and therefore may have the same issue. It is best to use elevated female IDC connector if used with PAL Apple IIe (for example https://fr.farnell.com/en-FR/samtec/esq-113-44-t-d/connect-femelle-26-voies-2-rangs/dp/2779437).
### status
done, working.

## PC Compatible keyboard
<img src="images/IMG_3034.jpeg" height="200">
This cable is based on a "PS2 extension cable for keyboard and mouse" (like https://amzn.eu/d/a3pizTv) cut approximately 50 cm after the female connector. An 5 pins JST connector (molex connector alternative) is connected to the cables. The female connector is glued into a 3D printed mounting enclosure that can be attached to one of the db9 or db25 (2 versions available) cutouts on the back of the Apple IIe. This first version of the connector need an AT (PS/2) keyboard able to use the XT protocol. Not all AT keyboards are capable to use this protocol, rare older AT keyboards have automatic or manual switching capabilities from AT to XT protocol.  
<p>
/!\ An active protocol translator for using a ps/2 keyboard as an XT keyboard can be found here: https://github.com/asig/ps2-to-xt-adapter/tree/master. Work is done to integrate it on a small PCB directly pluggable onto the PCT card.
</p>

### Molex connector
<pre>
____
|5||   +5V
|4||   GND
|3||
|2||   Data
|1||   Clock
----
(cable connector - frond view)
</pre>

### PS/2 Connector
<pre>
    6  N  5
   4       3
     2   1
(socket/female - front view)

Pin   Function
 1    Data
 2    NC
 3    GND
 4    +5V
 5    Clock
 6    NC
</pre>
### PS/2 Cable
<pre>
Molex  PS/2
 1  -  5
 2  -  1
(3  -  2) - 2 unused pins, connection not needed
 4  -  3
 5  -  4
       6
</pre>
### status
Cable: done, working  
XT/AT converter: done, working  
<img src="images/IMG_3143.jpeg" height="200">
<img src="images/IMG_3145.jpeg" height="200">

## Sound Connector
One or two Simple two wires (dupont) cable. Cheap female/female jumper wire can be used to connect motherboard J18 to PCT J1. If the speaker cable is long enough it can be connected directly to the J7 connector of the PCT card. If not, a cheap female/male jumper wire can be used.

### PCT Molex connector (J1 / J7)
<pre>
____
|2||   Sound signal
|1||   +5V
----
(front view)
</pre>

### Apple II speaker
<pre>
____
|2||   Sound signal
|1||   +5V
----
(front view)
</pre>

## GOTEK + flashfloppy as secondary drive in single TransDrive
3D printed enclosure, configuration and cables.

### Enclosure
<div><img src="images/IMG_3164.jpeg" width="300"></div>  
<div><img src="images/IMG_3166.jpeg" width="300"></div>  

[Gotek enclosure with OLED sceen](hardware/transdriveGotek/v0.0)

### Configuration
https://github.com/keirf/flashfloppy  

### Cables
The cable provided with the TransDrive isn't long enough to connect the Gotek. You need to find (or build) an other cable.  
(to do)

## useful links
PCT documentations and software  
https://ae.applearchives.com/all_apple_iis/pc_transporter/  

French PCT documentation  
http://www.apple-iigs.info/doc/fichiers/Brejoux_PC_Transporter%202.pdf  

Various PCT Pinouts and adaptaters (but not exhaustive)  
https://www.applefritter.com/appleii-box/harrowalsh.de/APPLEBOX/APPLE2/Manuals/AE%20PC%20Transporter%20ComponentsPinouts.pdf  

Pinouts, adapters and other resources  
https://osites.tripod.com/transport.html  

Schematics and PCB for 5.25" and 3.5" PC floppy drive adapter rebuild  
https://www.applefritter.com/appleii-box/H070_AppleIITransDriveAdaptor.htm  

Pinouts of various Apple II, Apple IIe, Apple IIc, Apple IIgs and Apple Printers connectors  
https://mirrors.apple2.org.za/ftp.apple.asimov.net/documentation/hardware/misc/Apple%20II%20Family%20Pinouts.pdf  

RGB TTL to RGB Analogic  
https://downloads.reactivemicro.com/Apple%20II%20Items/Hardware/Apple_II_AppleColor_TTI_RGB/TheMarcorlandiModification_TTLRGB.pdf  

Apple 2GS to SCART (for ColorSwitch to SCART)  
https://www.brutaldeluxe.fr/documentation/cortland/v3_03_Schematics.pdf  

For photos  
https://www.applefritter.com/content/applied-engineering-pc-transporter-and-drives  
