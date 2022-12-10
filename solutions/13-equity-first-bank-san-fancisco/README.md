# 13: Equity First Bank (San Fancisco)

<div align="center"><img src="EXAPUNKS - Equity First Bank (3008, 34, 10, 2022-12-10-23-51-16).gif" /></div>

## Instructions
> Dispense all available cash from all connected ATMs.
> 
> For more information see "Network Exploration: Equity First Bank" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; NAVIGATE TO ATM PLANE
LINK 800
LINK 800
LINK 800

; DUPE
REPL 801
REPL 802
REPL 803
REPL 804
REPL 805
REPL 806
LINK 800
JUMP BEGIN

; NAVIAGTIONS
MARK 801
LINK 801
JUMP BEGIN

MARK 802
LINK 802
JUMP BEGIN

MARK 803
LINK 803
JUMP BEGIN

MARK 804
LINK 804
JUMP BEGIN

MARK 805
LINK 805
JUMP BEGIN

MARK 806
LINK 806

; BEGIN
MARK BEGIN
; DISPENSE ALL CASH
MARK EMPTY_ATM
COPY 20 #DISP
TEST #CASH = 0
FJMP EMPTY_ATM
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 3008   | 34   | 10       |
