# 13: Equity First Bank (San Fancisco)

<div align="center"><img src="EXAPUNKS - Equity First Bank (3027, 14, 10, 2022-12-11-00-13-53).gif" /></div>

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
COPY 799 X
MARK DUPE
TEST X = 807
TJMP EMPTY_ATM
ADDI X 1 X
REPL DUPE
LINK X

; DISPENSE ALL CASH
MARK EMPTY_ATM
COPY 20 #DISP
TEST #CASH = 0
FJMP EMPTY_ATM
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 3027   | 14   | 10       |
