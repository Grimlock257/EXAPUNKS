# 19: Emerson's Guide (Streetsmarts GIS Database)

<div align="center"><img src="EXAPUNKS - Emerson's Guide (53, 43, 6, 2022-12-11-21-11-45).gif" /></div>

## Instructions
> Each host contains a list of restaurants and their ratings, from one to five stars (file 200). Locate the entry that corresponds to the Last Stop on Eddy Street and change its rating from one to five stars.
> 
> The name of the target restaurant and its location within the GIS grid is available in file 300. The first coordinate is the number of times to move east, while the second coordinate is the number of times to move north (positive) or south (negative).
> 
> For more information see "Network Exploration: Geographic Information Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; ENTER GIS
GRAB 300
LINK 800

; EASTWARD MOVEMENT
SEEK 1
COPY F X

MARK EAST_LOOP
TEST X = 0
TJMP NORTH_SOUTH_MOVE
LINK 801
SUBI X 1 X
JUMP EAST_LOOP

; NORTH/SOUTH MOVEMENT
MARK NORTH_SOUTH_MOVE
COPY F X

TEST X > 0
TJMP NORTH_LOOP
FJMP SOUTH_LOOP

; NORTH LOOP
MARK NORTH_LOOP
TEST X = 0
TJMP FIND_RESTAURANT
LINK 800
SUBI X 1 X
JUMP NORTH_LOOP

; SOUTH LOOP
MARK SOUTH_LOOP
TEST X = 0
TJMP FIND_RESTAURANT
LINK 802
ADDI X 1 X
JUMP SOUTH_LOOP

; MODIFY THE RATING
MARK FIND_RESTAURANT
SEEK -9999
COPY F X
WIPE

GRAB 200

MARK SEARCH_LOOP
TEST F = X
TJMP MODIFY
SEEK 5
JUMP SEARCH_LOOP

MARK MODIFY
COPY F X
COPY X F
COPY X F
COPY X F
COPY X F
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 53     | 43   | 6        |
