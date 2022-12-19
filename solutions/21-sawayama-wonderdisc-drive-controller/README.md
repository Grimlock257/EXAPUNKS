# 21: Sawayama Wonderdisc (Drive Controller)

<div align="center"><img src="EXAPUNKS - Sawayama WonderDisc (8719, 53, 122, 2022-12-19-22-41-46).gif" /></div>

## Instructions
> Modify your WonderDisc, which normally only plays SSEA region games, to play games from any region.
> 
> The SSEA region code is available in file 300.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Hardware Hacks: Sawayama WonderDisc" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; NAVIGATE TO CONTROL
GRAB 300
COPY F X
DROP

LINK 800

; AUTH
COPY 8 #AUTH
COPY 0 #AUTH
COPY 3 #AUTH
COPY 2 #AUTH
COPY 7 #AUTH
COPY 1 #AUTH
COPY 0 #AUTH
COPY 4 #AUTH
COPY 9 #AUTH
COPY 5 #AUTH
COPY 1 #AUTH
COPY 2 #AUTH
COPY 5 #AUTH
COPY 2 #AUTH
COPY 6 #AUTH

; GET TRACK FILE
MARK READ_TRACK
COPY #TRAK T
LINK 801
GRAB T

; SEND DATA
REPL MAKE_DUPLICATOR

MARK SEND_DATA
COPY F M
TEST EOF
FJMP SEND_DATA
COPY -1 M
HALT

; DUPLICATE FILE
MARK MAKE_DUPLICATOR
MAKE
MARK DUPLICATE_LOOP
COPY M F
SEEK -1
TEST F = -1
TJMP MOVE_TO_BUFFER
SEEK -1
TEST F > 0
FJMP REWRITE_REGION
TJMP DUPLICATE_LOOP

; REWRITE THE REGION
MARK REWRITE_REGION
SEEK -1
COPY X F
JUMP DUPLICATE_LOOP

; MOVE TO BUFFER
MARK MOVE_TO_BUFFER
SEEK -1
VOID F
LINK -1
LINK 800
DROP
LINK -1
JUMP READ_TRACK
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 8719   | 53   | 122      |
