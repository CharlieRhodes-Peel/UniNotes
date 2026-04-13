This page builds on previous diagrams presented in [[Control Signals]] covering a basic: single-cycle, in-order, single-issue [[CPU]] design. And how the issues with that design can be optimised
# Issue with ->[[Control Signals]]<- CPU design:
See [[Data Paths]] and [[Control Signals]] for example diagrams of these designs
- The critical path of the [[CPU]] is very long
- Have to wait for each combinatorial "piece" to finish for a single clock cycle to finish, i.e *longest delay determines clock period*
	- Can't vary clock period on a cycle-by-cycle basis! 
- the critical path goes through both instruction and data memory!
	- VERY SLOW CLOCK CYCLE SPEED

# Building up pipelined [[Data Paths]]
The following is very broken. It lays the foundation of a final pipe-lined result which will be covered in [[Pipelining]], here it will be built on. The reason this is done is that we can have an ultimately quicker clock-cycle speed.

Given a program that works on a single-cycle, in-order, single-issue [[CPU]] like that seen in [[Control Signals]], the program will not work on this basic implementation
![[Pasted image 20260219134117.png]]
- Breaking up the combinatorial path with registers so that each *section* completes in it's own clock cycle
- Each of the "yellow things" are a register / flip-flips

[[ISA]] used here is [[MIPS]]
##### For R-type instructions:
###### Fetch
- Instruction is held in pipeline register after the "fetch" part (*the first pipeline segment*)
###### Register Read (decode)
- Now the output of the two register values are held in the *second* *register* segment
###### Execution
- [[ALU]] result it put into the *third segment* 
###### Memory
- The [[ALU]] result is just copied along to *fourth segment* (as we are doing r-type, see [[MIPS]])
###### Write back
- Then we write back to the registers in the RegFile (look at the line going from the Mux after the *fourth segment* going back to the RegFile)


#### Simple Fix No.1
![[Pasted image 20260219135948.png]]
#### Simple Fix No.2
Pipelined [[Control Signals]]
![[Pasted image 20260219140159.png]]

# Adding Data Hazard Detection to Pipeline:
![[Pasted image 20260219172737.png]]
Hazard decetection deals with hazards that are "unfixable", forwarding unit deals with hazards that are "fixable"