# 17: Digital Library Project (Patron Access System)

<div align="center"><img src="EXAPUNKS - Digital Library Project (379, 35, 70, 2022-12-11-20-05-53).gif" /></div>

## Instructions
> Books are stored in the host corresponding to the first digit of their call number, while a book's file ID is 200 plus the last two digits of the call number. For example, book 512 would be stored in the host *500-599* as file 212.
> 
> Duplicate each of the books requested by EMBER-2 and bring them back to your host.
> 
> The call numbers for the books EMBER-2 wants are available in file 300.
> 
> Note that EMBER-2 will never request more than one book from the same host.

## Solution

### [XA](XA.exa) (local)
```asm
; MOVE TO GATEWAY
GRAB 300
LINK 800

; FOR EACH BOOK, DUPE
MARK DUPE_LOOP
COPY F X
REPL SEARCH
TEST EOF
FJMP DUPE_LOOP
WIPE
HALT

; SEARCH (CORRECT HOST)
MARK SEARCH
LINK 800
SUBI X 100 X
SWIZ X 3 T
TEST T = 0
FJMP SEARCH

; GRAB FILE
ADDI 200 X X
GRAB X

; SEND DATA
REPL MAKE_DUPLICATOR

MARK SEND_DATA
COPY F M
TEST EOF
FJMP SEND_DATA
COPY -1 M
HALT

; DUPLICATE BOOK
MARK MAKE_DUPLICATOR
MAKE
MARK DUPLICATE_LOOP
COPY M X
TEST X = -1
TJMP GO_HOME
COPY X F
JUMP DUPLICATE_LOOP

MARK GO_HOME
LINK -1
JUMP GO_HOME
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 379    | 35   | 70       |
