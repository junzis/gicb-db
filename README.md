# Database for world aircraft's common GICB capabilities

The common usage Ground-initiated Comm-B (GICB) capabilities refer to a set of Mode S transponder downlink capabilities that are often interested by air traffic controllers. They include, for example, ADS-B messages, Mode S enhanced surveillance replies, and Mode S meteorological reports.


This repository contains a dataset generated from the global Mode S data obtained by OpenSky receiver network. It is published to support the scientific paper for OpenSky 2020 Symposium: *Mode S Transponder Comm-B Capabilities in Current Operational Aircraft*. The process of data gathering and decoding is documented in this paper.


## Dateset structure

The dataset `data/gicb_db.csv` includes approximately 50,000 aircraft over the world. The structure of this dataset is illustrated with the following data fragment (with commas removed):


```
icao24  reg     type  05 06 07 08 09 0A 20 21 40 41 42 43 44 45 48 50 51 52 53 54 55 56 5F 60
......  ......  ....  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .
......  ......  ....  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .
48406f  PH-LAB  C550  1  1  1  1  1  1  1  0  1  0  0  0  0  0  0  1  0  0  1  0  0  0  1  1
4843de  PH-LAG  P28A  0  0  0  0  0  0  1  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
4850cf  PH-LAU  F9EX  1  1  1  1  1  1  1  0  1  0  0  0  0  0  0  1  0  0  1  0  0  0  1  1
4845e4  PH-LAV  BALL  0  0  0  1  0  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
4843e5  PH-LAW  C310  0  0  0  0  0  0  1  0  0  0  0  0  0  0  0  1  0  0  0  0  0  0  0  0
484c2d  PH-LAZ  BALL  0  0  0  1  0  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
48442f  PH-LBR  C208  0  0  0  1  0  0  1  0  1  0  0  0  0  0  0  1  0  0  0  0  0  0  0  0
4851f1  PH-LDS  C172  0  0  0  0  0  0  1  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
484737  PH-LEN  C172  0  0  0  0  0  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
485348  PH-LES  BALL  1  1  1  1  1  1  1  1  1  0  0  0  0  0  0  1  1  1  0  0  0  0  1  1
484779  PH-LFA  C172  0  0  0  1  0  0  1  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
......  ......  ....  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .
......  ......  ....  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .  .
```

The first three columns are **transponder address**, **aircraft registration**, and **aircraft typecode**. The remaining columns are Comm-B Data Selector (BDS) codes, which correspond to specific GICB capabilities. When a value is set to `1`, the corresponding aircraft is capable of transmitting this type of downlink messages.

## Common BDS codes

The relationships between BDS code and specific Mode S downlink messages are shown in the following table:

```
BDS  Message                                         
-------------------------------------------------------
05   Extended squitter airborne position             
06   Extended squitter surface position              
07   Extended squitter status                        
08   Extended squitter identification and category   
09   Extended squitter airborne velocity information 
0A   Extended squitter event-driven information      
20   Aircraft identification                         
21   Aircraft registration number                    
40   Selected vertical intention                     
41   Next waypoint identifier                        
42   Next waypoint position                          
43   Next waypoint information                       
44   Meteorological routine report                   
45   Meteorological hazard report                    
48   VHF channel report                              
50   Track and turn report                           
51   Position coarse                                 
52   Position fine                                   
53   Air-referenced state vector                     
54   Waypoint 1                                      
55   Waypoint 2                                      
56   Waypoint 3                                      
5F   Quasi-static parameter monitoring               
60   Heading and speed report                        

```

## Additional information

1. Checkout [pyModeS](https://github.com/junzis/pyModeS/) to see how Mode S message can be decoded.

1. Use the [OpenSky aircraft database](https://opensky-network.org/aircraft-database) to query more information about each aircraft.