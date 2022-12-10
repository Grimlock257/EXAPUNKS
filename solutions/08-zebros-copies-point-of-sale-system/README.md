# 8: Zebros Copies (Point-Of-Sale System)

<div align="center"><img src="EXAPUNKS - Zebros Copies (110, 29, 3, 2022-12-10-20-03-00).gif" /></div>

## Instructions
> Erase Ghast's debt to the copy shop by zeroing out his balance in the customer database (file 200) and appending a payment to the payment log (file 201) with today's date and the exact amount of his prior balance.
> 
> Ghast's customer ID is available in file 300.
> 
> For more information see "Network Exploration: Digicash Point-of-Sale Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
NOTE NAVIGATE
GRAB 300
COPY F X
DROP
LINK 800
NOTE ZERO BALANCE
GRAB 200
MARK SEARCHGHAST
TEST F = X
FJMP SEARCHGHAST
COPY F M
SEEK -1
COPY 0 F
COPY F M
SEEK -1
COPY 0 F
DROP
NOTE ADD TRANSACTION
GRAB 201
SEEK 9999
LINK 801
COPY #DATE F
COPY X F
LINK -1
COPY M F
COPY M F
HALT


```

### [XB](XB.exa) (global)
```asm
COPY M X
COPY M T
COPY X M
COPY T M
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 110    | 29   | 3        |
