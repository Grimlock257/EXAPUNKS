# 9: SFCTA Highway Sign #4902 (Remote Access Interface)

<div align="center"><img src="EXAPUNKS - SFCTA Highway Sign #4902 (166, 10, 1, 2022-12-10-20-06-11).gif" /></div>

## Instructions
> Write EMBER-2's message (file 300) to the highway sign. The file contains one character value for each position on the sign from left to right, top to bottom.
> 
> For more information see "Hardware Hacks: Electronic Highway Signs" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
MARK LOOP
DIVI X 9 #DATA
MODI X 9 #DATA
ADDI 1 X X
COPY F #DATA
TEST EOF
FJMP LOOP
NOTE LEAVE NO TRACE
WIPE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 166    | 10   | 1        |
