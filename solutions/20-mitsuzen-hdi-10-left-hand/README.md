# 20: Mitsuzen HDI-10 (Left Hand)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (105, 71, 12, 2022-12-12-20-32-42).gif" /></div>

## Instructions
> There are three nerve signals that need to be relayed: muscle control (M), which runs from your central nervous system (CNS) to your hand (HND), and heat (H) and pressure (P), which run the other direction.
> 
> For each signal, read a value from the input nerve and relay it to the output nerve. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; CNS
LINK 800
LINK -3
LINK -3

REPL H_CNS
REPL P_CNS

JUMP M_CNS

; H_CNS
MARK H_CNS
LINK -3
NOOP

MARK H_CNS_LOOP
COPY M #NERV
NOOP
NOOP
NOOP
NOOP
JUMP H_CNS_LOOP

; P_CNS
MARK P_CNS
LINK -3
LINK -3

MARK P_CNS_LOOP
NOOP
NOOP
COPY M #NERV
NOOP
NOOP
JUMP P_CNS_LOOP

; M_CNS
MARK M_CNS
NOOP

MARK M_CNS_LOOP
NOOP
NOOP
NOOP
NOOP
COPY #NERV M
JUMP M_CNS_LOOP
```

### [XB](XB.exa) (global)
```asm
; HND
LINK 800
NOOP ; WAIT FOR XA
LINK 3
LINK 3

REPL H_HND
REPL P_HND

JUMP M_HND

; H_HND
MARK H_HND
LINK 3
NOOP

MARK H_HND_LOOP
COPY #NERV M
NOOP
NOOP
NOOP
NOOP
JUMP H_HND_LOOP

; P_HND
MARK P_HND
LINK 3
LINK 3

MARK P_HND_LOOP
NOOP
NOOP
COPY #NERV M
NOOP
NOOP
JUMP P_HND_LOOP

; M_HND
MARK M_HND
NOOP

MARK M_HND_LOOP
NOOP
NOOP
NOOP
NOOP
COPY M #NERV
JUMP M_HND_LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 105    | 71   | 12       |
