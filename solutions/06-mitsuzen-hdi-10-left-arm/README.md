# 6: Mitsuzen HDI-10 (Left Arm)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (241, 23, 6, 2022-12-10-20-01-26).gif" /></div>

## Instructions
> Read a value from the nerve connected to your central nervous system (CNS) and relay it to the nerve connected to your arm (ARM), clamping the value so that it never goes below -120 or above 50. Repeat _ad infinitum_.
> 
> Since this task takes place inside a network you control— that is, your own body— it is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> Note that #NERV is a _hardware register_, not a file. You can use it directly in your code like any other register.
> 
> For more information about the phage see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK READ
COPY #NERV X
TEST X > 50
TJMP HIGH
TEST X < -120
TJMP LOW
COPY X M
JUMP READ
MARK HIGH
COPY 50 M
JUMP READ
MARK LOW
COPY -120 M
JUMP READ
```

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 1
LINK 1
LINK 1
LINK 1
MARK LOOP
COPY M #NERV
JUMP LOOP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 241    | 23   | 6        |
