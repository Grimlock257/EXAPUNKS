# 2: Valhalla (=Plastered)

<div align="center"><img src="EXAPUNKS - Valhalla (=plastered, 2022-12-11-21-27-01).gif" /></div>

## Instructions
> To win this battle you must control a majority of the hosts for as long as possible. 
> 
> To take control of a host, write any value to its #CTRL register. Reading from a #CTRL register will tell if you (1) or your opponent (-1) controls the host.
> 
>      Gain one point every cycle you control more hosts than your opponent.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
; NAVIGATE TO START
LINK 800
LINK -1

; WAIT FOR ENEMY
@REP 16
NOOP
@END
KILL

; FOWARD LOOP
MARK START_FORWARD
COPY 9 X
MARK FORWARD_LOOP
COPY 1 #CTRL
LINK 800
SUBI X 1 X
TEST X = 0
FJMP FORWARD_LOOP
TJMP START_BACKWARD

; BACKWARD LOOP
MARK START_BACKWARD
COPY 9 X
MARK BACKWARD_LOOP
COPY 1 #CTRL
LINK -1
SUBI X 1 X
TEST X = 0
FJMP BACKWARD_LOOP
TJMP START_FORWARD


```

