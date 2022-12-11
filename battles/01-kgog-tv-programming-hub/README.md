# 1: KGOG-TV (Programming Hub)

<div align="center"><img src="EXAPUNKS - KGOG-TV (mutex8021, 2022-12-11-16-45-42).gif" /></div>

## Instructions
> To win this battle you must make your movies play for longer than your opponent's. A movie will play when that movie's file is the only movie file sitting in a *channel* host.
> 
>      Gain one point every cycle for each of your movies that is playing (files 210 and 211).
> 
>      Lose one point every cycle that a movie file that isn't yours (files 230, 231, and 265) is held by an EXA you control or is sitting in your host.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> Note that you may only battle your Steam friends after beating the NPC opponent. To view the list of possible opponents, click the "SELECT OPPONENT" button above.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; STALL TIME
NOOP
NOOP
; NOOP

; NAVIGATE TO STORAGE
LINK 800

; DUPE
REPL CH_26
REPL CH_67

; CH-9
MARK CH_9
GRAB 210
LINK 809
DROP
GRAB 265
LINK -1
DROP
HALT

; CH-26
MARK CH_26
GRAB 211
LINK 828
DROP
GRAB 230
LINK -1
DROP
HALT

; CH-67
MARK CH_67
LINK 867
GRAB 231
LINK -1
DROP
HALT
```

