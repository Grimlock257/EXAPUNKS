# 16: TEC Redshift (Development Kit)

<div align="center"><img src="EXAPUNKS - TEC Redshift™ (9919, 33, 5, 2022-12-11-17-10-53).gif" /></div>

## Instructions
> There is an unknown three-digit code (such as 4-7-3) that, when entered one digit at a time into #PASS, will unlock the link between *debug* and *secret*. Find the three-digit code and create a file in your host that contains the code as a sequence of three values, followed by the development kit's RDK ID.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800

; ENTER COMBO
MARK LOOP

; SEE IF EXA SURVIVED
TEST MRD
TJMP WRITE_FILE

; INCREMENT
ADDI X 1 X

SWIZ X 0003 #PASS
SWIZ X 0002 #PASS
SWIZ X 0001 #PASS

; CHECK IF EXISTS
REPL ATTEMPT_LINK
TEST MRD
TJMP WRITE_FILE

JUMP LOOP

MARK ATTEMPT_LINK
LINK 800
COPY 1 M
HALT

; CREATE FILE
MARK WRITE_FILE
VOID M
MAKE
SWIZ X 0003 F
SWIZ X 0002 F
SWIZ X 0001 F

LINK 800
DROP
GRAB 199
COPY F X
DROP
GRAB 400
SEEK 9999
COPY X F

LINK -1
LINK -1
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 9919   | 33   | 5        |
