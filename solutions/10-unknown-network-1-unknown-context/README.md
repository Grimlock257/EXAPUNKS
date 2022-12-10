# 10: Unknown Network 1 (Unknown Context)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 1 (30, 22, 27, 2022-12-10-20-07-04).gif" /></div>

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
ADDI 1 X X
JUMP TESTEND

MARK LEFT
LINK 800
ADDI 1 X X
JUMP TESTEND

MARK TESTEND
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
| 30     | 22   | 27       |
