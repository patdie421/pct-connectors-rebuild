# pct-connectors-rebuild
In this repository I will consolidate all the elements which will allow you to use an "AE PC Transporter" card in an Apple IIe or IIgs. In particular, elements allowing you to recreate the cables and connectors which are generally lost when one of these cards is found.  
The data comes from different sources available on Internet. I will try to reference them all in the "useful links" section.  

<div style="text-align:center;">

![figure 1: PC Transporter rev D](images/image.png)  
<p>figure 1: PC Transporter rev D</p>
</div>

<div style="text-align:center;">

![figure 2: Apple IIe motherboard](images/IMG_3023.jpeg)  
<p>figure 2: Apple IIe motherboard</p>
</div>

## Connector locations  
<div style="text-align:center;">

![figure 3: PC Transport connector location](images/IMG_3021.jpeg)
<p style="text-align:center;">figure 3: front view card diagram with connector locations</p>
<pre>
J1 - Apple II Speaker motherboard connector (INPUT)
J2 - Composite video (OUTPUT)
J3 - IIe keyboard adapter (INPUT)
J4 - PC Transporter Disk drive (INPUT/OUTPUT)
J5 - PC Compatible keyboard (XT/AT or PS/2) (INPUT)
J6 - ColorSwitch (OUTPUT)
J7 - Apple II Speaker (OUTPUT)
J8 - Coprocessor socket
</pre>
</div>

## Video Composite output
[to do]


## CGA Video cable (AE Digital RGB Adapter)
<img src="images/IMG_3006.jpeg" height="200">

This cable is to use to output video signal directly to a CGA compatible monitor (TTL monitor). Apple II and PCT card can't share easily the same connection for this kind of video connection.

One side is a DB9 Male connector.
Other one a "10 pins male IDC connector".

Ribbon cable mount connectors are the best way to make this cable. Some parts that could be used :

- https://fr.farnell.com/en-FR/wurth-elektronik/61201025821/plug-idc-2-54mm-strain-relief/dp/2356318
- https://fr.farnell.com/en-FR/multicomp-pro/8ftm09p-30n1-fec/plug-idc-d-threaded-9way/dp/1099306

### status
done, working.

### 10 pin IDC Male  
<img src="images/IMG_2977.jpeg" width="300">
<pre>
(front side)  
____________________   
| 2   4   6   8  10|  
| 1   3   5   7   9|  
--------|   |-------  
  |1             |  
  |ribbon  cables|  
  
1 GND
2 Intensity
3 (NC for CGA)
4 (NC for CGA)
5 Red
6 HS
7 Green
8 VS
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
(front side)

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
IDC    DB9  
1  --  1  
2  --  6  
3      2  
4      7  
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
You can have cristal clear output on HDMI monitor by using RGBtoHDMI (https://github.com/hoglet67/RGBtoHDMI). The profile to use is : [to add]  
<img src="images/IMG_3022.jpeg" width="400">

## Storage connector
<img src="images/IMG_2981.jpeg" height="200">

### 20 pin IDC Female  
<pre>
(front side)  
_________________________________________   
| 2   4   6   8  10  12  14  16  18  20 |  
| 1   3   5   7   9  11  13  15  17  19 |  
------------------|   |------------------  
  |1                                  |  
  |           ribbon cables           |  
</pre>
### DB19 Female
<pre>
   |                            |
   |1___________________________|
  /  11 12 13 14 15 16 17 18 19  \  
 /  1  2  3  4  5  6  7  8  9  10 \
------------------------------------  
(front side)

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

## Apple 2e keyboard adapter

[to do]
### connections

(schema)

### PCB

[to do]

## PC Compatible keyboard

### Molex connector
<pre>
____
|1||   Clock
|2||   Data
|3||
|4||   GND
|5||   +5V
----
</pre>
### PS/2 Connector
<pre>
    6  N  5
  4         3
     2   1
(socket/female)
</pre>
### PS/2 Cable
<pre>
Molex  PS/2
1  -   5
2  -   1
3  -   2
4  -   3
5  -   4
       6
</pre>

## Video
### Molex connector
<pre>
____
|1||   GND
|2||   Video Composite (NTSC)
----
</pre>
### Apple II internal Video Connector (J13)
<pre>
(connectors side)
___________
| 1 2 3 4 |
===========
(keyboard side)

1  GND
2  Video Composite (NTSC or PAL)
3  -5V
4  +12V
</pre>

### Video Cable
<pre>
Molex  PS/2
1  -   1
2  -   2
   -   3
   -   4

</pre>
## useful links
https://ae.applearchives.com/all_apple_iis/pc_transporter/pc_transporter_manual_131.pdf  
https://www.applefritter.com/appleii-box/harrowalsh.de/APPLEBOX/APPLE2/Manuals/AE%20PC%20Transporter%20ComponentsPinouts.pdf  
https://osites.tripod.com/transport.html  
https://www.applefritter.com/appleii-box/H070_AppleIITransDriveAdaptor.htm  
https://www.applefritter.com/content/applied-engineering-pc-transporter-and-drives  

