# 5: Euclid's Pizza (Order System)

<div align="center"><img src="EXAPUNKS - Euclid's Pizza (13, 16, 1, 2022-12-10-20-00-34).gif" /></div>

## Instructions
> Append your order (file 300) to the end of the order list (file 200).
> 
> Note that all orders, including yours, will consist of exactly five keywords.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F M
COPY F M
COPY F M
COPY F M
COPY F M
HALT
```

### [XB](XB.exa) (global)
```asm
LINK 800
GRAB 200
SEEK 9999
COPY M F
COPY M F
COPY M F
COPY M F
COPY M F
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 13     | 16   | 1        |
