# 10: Unknown Network 1 (Unknown Context)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 1 (30, 21, 27, 2022-12-10-20-25-10).gif" /></div>

## Instructions
> Find file 276 in the network and bring it back to your host.
> 
> Note that an EXA cannot grab a file that is being held by another EXA.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800

MARK DUPE
REPL RIGHT
JUMP LEFT

MARK RIGHT
LINK 801
JUMP TESTEND

MARK LEFT
LINK 800
JUMP TESTEND

MARK TESTEND
ADDI 1 X X
TEST X = 3
FJMP DUPE

NOTE END
KILL
GRAB 276
LINK -1
LINK -1
LINK -1
LINK -1
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 30     | 21   | 27       |
