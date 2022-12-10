# 12: Workhouse (Work Management System)

<div align="center"><img src="EXAPUNKS - WorkHouse (544, 49, 2, 2022-12-10-22-45-50).gif" /></div>

## Instructions
> Locate EMBER-2's user file in the *users* host and overwrite it so that the sum of the values is the same but no individual value exceeds $75. All values, except for the last, must be the maximum value ($75). You will need to add additional values to accomplish this.
> 
> EMBER-2's username is available in file 300.
> 
> Note that the sum of the values in EMBER-2's account will always be less than $10,000.
> 
> For more information see "Network Exploration: Workhouse" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; GET USERNAME
GRAB 300
COPY F X
DROP
; IDENTIFY USER FILE IDS
LINK 800
GRAB 199
MARK FIND_USER
TEST F = X
TJMP GET_FILE_ID
SEEK 2
FJMP FIND_USER
MARK GET_FILE_ID
SEEK 1
COPY F X
DROP
; NAVIGATE TO USERS
LINK 799
; SAVE USER ID
MAKE
COPY X F
DROP
; OPEN USERS FILE
GRAB X
; SUM EXISTING VLAUES
SEEK 2
COPY 0 X
MARK SUM_VALUES
ADDI F X X
TEST EOF
FJMP SUM_VALUES
; SAVE MODULO IN FILE
DROP
GRAB 400
SEEK 9999
MODI X 75 F
SEEK -9999
COPY F T
DROP
GRAB T
; SEEK TO START OF VALUE
; SEEK -9999
SEEK 2
; REWRITE IN $75 BLOCKS
DIVI X 75 X
MARK WRITE_75
COPY 75 F
SUBI X 1 X
TEST X = 0
FJMP WRITE_75
; WRITE THE MODULO
DROP
GRAB 400
COPY F X
COPY F T
WIPE
GRAB X
SEEK 9999
COPY T F
HALT

```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 544    | 49   | 2        |
