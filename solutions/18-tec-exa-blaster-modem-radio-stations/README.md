# 18: TEC EXA-Blaster Modem (Radio Stations)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster� Modem (652, 43, 11, 2022-12-11-20-48-00).gif" /></div>

## Instructions
> ﻿Connect to each radio station and replace every song in the playlist (file 200) with ‗CAN'T (NOT) GET OVER YOU‗ by ‗ME2U‗ (file 300). Each song in a playlist consists of two keywords: the song name and the artist name.
> 
> A list of phone numbers for the radio stations is available in file 301.
> 
> Note that EXAs in global mode can only communicate if there is a path of links connecting them.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; MOVE TO RUNWAY
GRAB 300
LINK 800
DROP
LINK -1

GRAB 301
LINK 800

; DIAL
MARK DIAL_LOOP
COPY 11 X
MARK DIAL
TEST EOF
TJMP WIPE
COPY F #DIAL
SUBI X 1 X
TEST X = 0
FJMP DIAL
REPL ENTER_STATION
NOOP
NOOP
NOOP
NOOP
COPY -1 #DIAL
JUMP DIAL_LOOP

MARK WIPE
WIPE
GRAB 300
WIPE

HALT

; ENTER STATION
MARK ENTER_STATION
GRAB 300
COPY F X
COPY F T
DROP

LINK 800
GRAB 200

; REPLACE
JUMP WRITE_LOOP

MARK RESET_T
SEEK -1
COPY F T

MARK WRITE_LOOP
COPY X F
COPY T F
TEST EOF
FJMP RESET_T
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 652    | 43   | 11       |
