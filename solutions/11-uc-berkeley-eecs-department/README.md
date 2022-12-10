# 11: UC Berkeley (EECS Department)

<div align="center"><img src="EXAPUNKS - UC Berkeley (428, 33, 7, 2022-12-10-21-18-51).gif" /></div>

## Instructions
> ﻿Locate the specified host (either *tape-1*, *tape-2*, or *tape-3*), and then locate the specified entry (‗ПАСЬЯНС‗) in the tape backup file in that host (file 200). Create a file in your host containing the entry's data.
> 
> The names of the target host and entry are available in file 300.
> 
> For more information see "Accessing Data in Legacy Storage Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
NOTE FIND HOST
MARK SEARCH_HOST
LINK 800
HOST X
SEEK -9999
TEST X = F
FJMP SEARCH_HOST
NOTE FIND ENTRY
COPY F X
WIPE
GRAB 200
MARK SEARCH_ENTRY
TEST F = X
FJMP SEARCH_ENTRY
NOTE FOUND ENTRY
COPY F T
COPY F X
NOTE READ DATA
SEEK -9999
SEEK T
MARK READ_DATA
COPY F M
SUBI X 1 X
TEST X = 0
FJMP READ_DATA
NOTE GOT DATA, DIE
COPY -1 M
HALT
```

### [XB](XB.exa) (global)
```asm
MAKE
NOTE WRITE ALL DATA
MARK WRITE_DATA
COPY M X
TEST X = -1
TJMP END
COPY X F
JUMP WRITE_DATA
MARK END
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 428    | 33   | 7        |
