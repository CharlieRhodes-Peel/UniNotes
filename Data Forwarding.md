Data forwarding is a way to help Data [[Pipelining]] hazards (see the hazard section of pipelining) by using values as **SOON** as they are computed

# Forwarding Paths:
![[Pasted image 20260219164951.png]]
## Forwarding Conditions:
##### EX hazard:
- if (EX/MEM.RegWrite AND (EX/MEM.RegR != 0) AND (EX/MEM.RegRD = ID/EX.RegRT)) 
	- then {ForwardA = 10 (binary, not 10)}
- if (EX/MEM.RegWrite AND (EX/MEM.RegR != 0) AND (EX/MEM.RegRD = ID/EX.RegRS)) 
	- then {ForwardB = 10 (binary, not 10)}
##### MEM harzard:
- if (MEM/WB.RegWrite AND (MEM/WB.RegRD != 0) AND (MEM/WB.RegRD = ID/EX.RegRS) and not (EX hazard)) 
	- then {ForwardA = 01}
- - if (MEM/WB.RegWrite AND (MEM/WB.RegRD != 0) AND (MEM/WB.RegRD = ID/EX.RegRT)) and not (EX hazard)) 
	- then {ForwardB = 01}
### What if two hazard occur at the same time?
consider the following:
```
add $1, $1, $2
add $1, $1, $3
add $1, $1, $4
```
- Want to use the most recent
- So we ONLY forward if the EX hazard is not true, hence in the MEM hazard section above it says (and not (EX hazard))
# Analysing the problem
Below diagram describes data forwarding **NEEDED** in the following assembly program, because as you can see, it's broken:
```
sub $2, $1, $3     # sub value calculated at reg 2
and $12, $2, $5    # reg 2 used in the "and" calc
or $13, $6, $2     # reg 2 using in the "or" calc
add $14, $2, $2    # reg 2 used twice in the add calc
sw $15, 100($2)    # stores value at offset of value $2 by 100
```
![[Pasted image 20260219161606.png]]

# Detecting the need to forward:
Summary: You're asking "Is there an instruction ahead of me in the pipline (in EX/MEM or MEM/WB stages (see [[MIPS]], pipelining section, for what this means)) that is about to write a value i need?"
If yes -> forward that value directly to the [[ALU]] instead of using what's in the [[Register]] file
- Can do this by passing [[Register]] numbers along pipeline
	- e.g ID/EX.RegRS = [[Register]] number for [[Register]] RS sitting in ID/EX pipeline register
	- ^ Example above is a "*tag*" name for an [[Instruction]]
- ALU operand register numbers in EX stage: given by
	- ID/EX.RegRS, ID/EX.RegRT.
## When is forwarding needed?
When Data Hazards can occurs. Data Hazards occurs at:
1a. **ID/EX.RegRS** = **EX/MEM.RegRD**
1b. **ID/EX.RegRT** = **EX/MEM.RegRD**
2a. **ID/EX.RegRS** = **MEM/WB.RegRD**
2b. **ID/EX.RegRT** = **MEM/WB.RegRD**
Essential during the execution -> memory pipeline register or the memory -> write back pipeline register
![[Pasted image 20260219165034.png]]
