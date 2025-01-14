# pct-connectors-rebuild

## Video Composite output

[to do]


## CGA Video cable (AE Digital RGB Adapter) - not tested now

(photo)

This cable is to use to output video signal directly to a CGA compatible monitor (TTL monitor). Apple II and PCT card can't share easily the same connection for this kind of video connection.

One side is a DB9 Male connector.
Other one a "10 pins male IDC connector".

Ribbon cable mount connectors are the best way to make this cable. Some parts that could be used :

- (https://fr.farnell.com/en-FR/wurth-elektronik/61201025821/plug-idc-2-54mm-strain-relief/dp/2356318)
- (https://fr.farnell.com/en-FR/multicomp-pro/8ftm09p-30n1-fec/plug-idc-d-threaded-9way/dp/1099306)

Connectors pinout :

### IDC Male  
(front side)  
<pre>
____________________   
| 1   3   5   7   9|  
| 2   4   6   8  10|  
---  ----------  ---  
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

### DB9 Male
(front side)
<pre>
  |ribbon |
  |cables |
  |1______|
 / 6 7 8 9 \
/ 1 2 3 4 5 \
-------------

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

## Apple 2e keyboard adapter

[to do]
### connections

(schema)

### PCB

[to do]
