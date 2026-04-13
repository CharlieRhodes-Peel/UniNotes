- We want to maximise instructions completed per second
- Only the simplest [[Microcontroller]]s are **not** pipelined
# Pipeline speedup:
- Assuming that all stages are balanced
	- i.e **critical** path of all stages are about the same
	- time between piped instructions = time between instructions (non pipelined) / number of stages
- If stages are not balanced then the speedup is slower
- The **speedup** is due to increased *throughput*!!
	- latency (time for each instruction) does not decrease (actually increases latency!)

## Hazard: When a current [[Instruction]] depends on a previous [[Instruction]]
This section is based off the assumption of using a [[MIPS]] [[ISA]], Pipelining stages are listed in [[MIPS]]
### Structural Hazard
- Required resource is busy
##### How to fix:
- Separate instruction / data memories
- or separate instruction / data **caches** but shared memory
### Data Hazard
- Wait for previous instruction to complete its data read/write
	- ```
		  add $s0, $t0, $t1
		  sub $t2, $s0, $t3
	  ```
##### How to fix:
- Can *stall* the clock cycle until the value is calculated and put in the correct place creating a "**bubble**"
	- Not ideal however, as is a very common piece of code and present a huge slow down, not always avoidable!
	- **HOWEVER** is avoidable at the **compiler** level rather than hardware
- Can do [[Data Forwarding]] or **Bypass**:
	- Using the result as **SOON** as its computed
		- i.e Take it out of the pipeline register:
		- However does require more connections:
		- ,

### Control Hazard
- Deciding on control action depends on previous instruction (branch issues)
- Can also have data hazards for branches when comparing recently updated values on a branch
##### How to fix:
- Bringing the decision of if it's a branch brought to as early as possible in the pipeline cycle, so we minimise "*wasted*" cycles
- [[Branch Prediction]]
- Other option (silly option): Stall on a branch

# Stalling a pipeline:
When there is absolutely nothing you can do about a hazard, then we need to stall a pipeline. Given the diagram in [[Data Forwarding]].
- Force control values in ID/EX register to 0 (see [[MIPS]] for desc)
	- EX, MEM and WB do nop (no-operation)
- Prevent update of PC and IF/ID register
	- Current instruction is decoded again
	- following instruction is fetched again
	- 1-cycle stall allows MEM to read data for lw
		- Will forward to EX stage in next cycle
![[Pasted image 20260219172619.png]]
## Delay slots: clawing back the stalls
- A taken branch always means one stall cycle
	- There is nothing we can do to get rid of it
	- so we might as well do something useful with it!
- i.e [[Instruction]] following a BRANCH is **ALWAYS** executed
# Building up a solution:
- The building blocks for the solution presented here is given in [[CPU Design Optimisations]]