# 4: Trash World News (Tutorial 4)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (407, 11, 2, 2022-12-10-19-59-57).gif" /></div>

## Instructions
> File 200 contains exactly one number, N. Create a new file in the *outbox* containing the numbers N through 0 in decreasing order. When you are finished, delete file 200.
> 
> For help completing this task see "Ghast Walks U Thru It" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
GRAB 200
COPY F X
WIPE
LINK 800
MAKE
MARK LOOP
COPY X F
SUBI X 1 X
TEST X = -1
FJMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 407    | 11   | 2        |
