# pct-connectors-rebuild
## Connector locations
![pct card](images/image.png) 
![pct card connectors](images/IMG_3021.jpeg)
## Video Composite output

[to do]


## CGA Video cable (AE Digital RGB Adapter)
<img src="images/IMG_3006.jpeg" height="200">
This cable is to use to output video signal directly to a CGA compatible monitor (TTL monitor). Apple II and PCT card can't share easily the same connection for this kind of video connection.

One side is a DB9 Male connector.
Other one a "10 pins male IDC connector".

Ribbon cable mount connectors are the best way to make this cable. Some parts that could be used :

- (https://fr.farnell.com/en-FR/wurth-elektronik/61201025821/plug-idc-2-54mm-strain-relief/dp/2356318)
- (https://fr.farnell.com/en-FR/multicomp-pro/8ftm09p-30n1-fec/plug-idc-d-threaded-9way/dp/1099306)

Connectors pinout :

### IDC Male  
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
<img src="images/IMG_3007.jpeg" width="200">
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

### Connections
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
### Bonus
You can have cristal clear output on HDMI monitor by using RGBtoHDMI (https://github.com/hoglet67/RGBtoHDMI). The profile to use is : [to add]  
<img src="images/IMG_3022.jpeg" width="400">
## Apple 2e keyboard adapter

[to do]
### connections

(schema)

### PCB

[to do]

## Refs
https://ae.applearchives.com/all_apple_iis/pc_transporter/pc_transporter_manual_131.pdf
https://www.applefritter.com/appleii-box/harrowalsh.de/APPLEBOX/APPLE2/Manuals/AE%20PC%20Transporter%20ComponentsPinouts.pdf

