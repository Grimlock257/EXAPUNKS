# 16: TEC Redshift (Development Kit)

<div align="center"><img src="EXAPUNKS - TEC Redshift™ (7938, 31, 4, 2022-12-11-19-21-20).gif" /></div>

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
TJMP DIE

; INCREMENT
ADDI X 1 X

SWIZ X 0003 #PASS
SWIZ X 0002 #PASS
SWIZ X 0001 #PASS

; CHECK IF EXISTS
REPL ATTEMPT_LINK
JUMP LOOP

MARK ATTEMPT_LINK
LINK 800
COPY 1 M

; CREATE FILE
MARK WRITE_FILE
MAKE
SWIZ X 0003 F
SWIZ X 0002 F
SWIZ X 0001 F

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

MARK DIE
VOID M
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 7938   | 31   | 4        |
