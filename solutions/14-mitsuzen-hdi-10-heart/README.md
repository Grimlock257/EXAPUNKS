# 14: Mitsuzen HDI-10 (Heart)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (158, 30, 29, 2022-12-11-11-54-00).gif" /></div>

## Instructions
> Read a value from the nerve connected to your central nervous system (CNS) and make your heart beat by writing a sequence of values to your sinoatrial (SA-N) and atrioventricular (AV-N) nodes as indicated in the HDI-10 I/O log when holding the "SHOW GOAL" button. The length of each sequence of values should be equal to the value from the CNS divided by -10. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; CNS
LINK 800

; SEQUENCE LENGTH
MARK READ_LOOP
DIVI #NERV -10 X

; DUPE
REPL SA_N
REPL AV_N

; NO-OP UNTIL ALL DONE
MARK NO_OP_LOOP
SUBI X 1 X
TEST X = 0
TJMP READ_LOOP
NOOP
FJMP NO_OP_LOOP

; SA-N
MARK SA_N
LINK 1
LINK 1

COPY 40 #NERV
COPY -70 #NERV

SUBI X 2 X

JUMP WRITE_LOOP

MARK AV_N
LINK 3
LINK 3

COPY -70 #NERV
COPY 40 #NERV

SUBI X 2 X

JUMP WRITE_LOOP

; WRITE LOOP
MARK WRITE_LOOP
COPY -70 #NERV
SUBI X 1 X
TEST X = 0
FJMP WRITE_LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 158    | 30   | 29       |
