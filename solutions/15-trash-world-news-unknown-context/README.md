# 15: Trash World News (Unknown Context)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (569, 29, 4, 2022-12-11-15-49-18).gif" /></div>

## Instructions
> ﻿Find and replace the keywords in the target message (file 212) as directed by EMBER-2.
> 
> A list of keyword pairs indicating which words should be found and what they should be replaced with is available in file 300. For example, the keyword ‗AI‗ should be replaced with the keyword ‗COLLECTIVE‗. Each keyword will only occur once, but may occur in any order.
> 
> Also, move file 200 to the *outbox*.

## Solution

### [XA](XA.exa) (global)
```asm
; NAVIGATE TO GHAST
LINK 800
LINK 799

GRAB 212

COPY M X

; SEARCH LOOP
MARK LOOP

; SEARCH 212 FOR KW
COPY M X
MARK SEARCH_KW
TEST F = X
FJMP SEARCH_KW

; REPLACE WORD
SEEK -1
COPY M F

; CHECK IF MORE
TEST M = 1
FJMP TERMINATE

; MOVE TO START
SEEK -9999
JUMP LOOP

; TERMINATE
MARK TERMINATE
HALT
```

### [XB](XB.exa) (global)
```asm
GRAB 300

; SEARCH LOOP
MARK LOOP

COPY 1 M

; SEARCH WORD
COPY F M

; SEARCH REPLACEMENT
COPY F M

TEST EOF
FJMP LOOP

; NO MORE WORDS
COPY -1 M
DROP

; MOVE TO OUTBOX
LINK 800
GRAB 200
LINK 800
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 569    | 29   | 4        |
