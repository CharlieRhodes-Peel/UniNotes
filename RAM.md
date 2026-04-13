# Summary
Memory, it rember stuff
## General Trends across all types of RAM
Bigger -> Slower and Faster -> Smaller
Bigger + Faster -> More expensive
Increasing the bandwidth increases the latency
Increasing the bandwidth also increases the [[Bus]] width

# Types of Memory
This section builds up different types of from their simplest to their most complex, starting with the latch. However if you just need a simple overview of it all look at the diagram below:
#### Diagram
![[Pasted image 20260309194305.png]]
## The Latch
- Very simple bi-stable circuit
- Often used **deep** inside a [[CPU]]

| Pros                          | Cons                           |
| ----------------------------- | ------------------------------ |
| Very few transistors needed   | Not (directly) clock sensitive |
| Extremely fast switching time | Makes design more difficult    |
### Diagram
![[Pasted image 20260309184753.png]]

## Flip-Flops
When you think of a register, least on the ELEC-course, when looking at things like (see [[Data Paths]] and [[Control Signals]]). It has been implicit that any [[Register]], or something to hold data. IS this flip flop circuit here. It is a buffered bi-stable circuit

| Pros                                  | Cons                     |
| ------------------------------------- | ------------------------ |
| Fast switching time                   | Much bigger than latches |
| Clock Edge sensitive                  |                          |
| Makes design easier                   |                          |
| Each bit is standalone (not an array) |                          |
![[Pasted image 20260309185140.png]]


## SRAM - Static RAM:
This is un-buffered RAM cell, another bi-stable piece of memory. Unlike flip-flops are un-buffered. Only really good for an array of these 
things. When we have been looking at [[Cache]] it is *implicit* that **THIS** is used

| Pros                                    | Cons                             |
| --------------------------------------- | -------------------------------- |
| Small (like latch)                      | Slower than latches & flip-flops |
| Easy to scale out into a grid           | Only efficient in arrays         |
| Uses same type of transistor as [[CPU]] | May require a memory controller  |
| Can provide **very** high **bandwidth** |                                  |

![[Pasted image 20260309185446.png]]

- Bits stored in on/off gates (uses 4-6 transistors)
- No charges to leak, no refreshing needed when powered

## DRAM - Dynamic RAM
Composed of a capacitor and a transistor

| Pros                                | Cons                                       |
| ----------------------------------- | ------------------------------------------ |
| Very high integration density       | Cell must be refreshed                     |
| Can build very large grids of cells | Even higher access latency                 |
| Very low cost per bit               | Latency is unpredictable                   |
|                                     | Can be difficult to integrate with [[CPU]] |
|                                     | Requires a complex memory controller       |


Capacitor charge represents a bit
- Capacitors need to "refresh"
switch connects it to the read or write circuit
### Typical 16 Mb DRAM chip:
**![[Pasted image 20231213163306.png]]**
#### Points:
- Bits stored as charge in capacitors
- Charges leak so need **refreshing** even when powered
- Simpler construction
- Smaller per bit
- Less expensive
- Slower (6-60ns) ~ 5 clock cycles ([[Cache]] are ~1ns)
- Used in our main memory

### DDR : Off-Chip DRAM
DDR stands for Double-Data Rate this is because DDR sends/receives data on both clock edges, doubling its bandwidth.

Computational logic and DRAM suit different fabrication processes
- DRAM processes: lots of very simple capacitors and transistors
- Compute processes: logs of logic gates, routing, and flip-flops
- Economically it is better to fabricate DDR as separate chips
#### DDR4:
34100 MB/s bandwidth

##### Packaging
- Has 288 pins
- Data lines (64 bits = 8 bytes)
- Control lines: read/write, select, refresh
- At 2Ghz clock, rate is about 16GiB/s
	- **Blocks** are read (e.g. 4k bits = 512 bytes) into a buffer

#### DDR5: (Current)
- Lower voltage (1.1V) -> lower power use
- faster clocks -> more bandwidth (up to 50 GiB/s)
- Two **INDEPENDENT** channels
- Some error correction built in (fixes data when it wrongly flips)
	- DRAM can loose data
	- Hard Failure
		- Permanent defect - most common
	- Soft Error
		- Random, non-destructive
		- No permanent damage to memory

### eDRAM : On-Chip DRAM
Gives the highest performance to DRAM when on the same chip as CPU. It's often used as very large L3 [[Cache]]
- Build it out of the same transistors as the [[CPU]]
- Connect CPU and eDRAM using intra-chip buses (see, AXI [[Bus]])

| Pros                                                 | Cons                                                               |
| ---------------------------------------------------- | ------------------------------------------------------------------ |
| Can get highg bandwidth useing wide intra-chip buses | Lower integration density due to CPU-oriented transistor processes |
| Reduces number of chips in the system                | Higher cost per bit than DRAM oriented chips                       |
### On-Package DRAM : HBM (high-bandwidth-memory)
The individual DRAM chips are on the same package as the [[CPU]]
![[Pasted image 20260309190930.png]]
- User access to the HBM stacks through AXI3 responder ports (see [[Bus]])
	- 16 independent 256-bit ports
	- Optional 32-bit data bus extension

# Unit of Transfer
- Internal
	- Usually governed by data [[Bus]] width
- External
	- Usually a block which is much larger than a word [[Bus]]
- Addressable unit
	- Smallest location which can be uniquely addressed

# Performance
 - Access time
	 - Time between presenting the [[address]] and getting the valid data (N clocks)- 
- Memory Cycle time
	- Time may be required for the memory to "recover" before next access
- Transfer rate
	- Data move rate

# Banks, Ranks and interleaving:
- Most [[CPU]]s use **TWO** 64 bit channels to the RAM
- Using 4 DDR4 DIMMs increase bandwidth (accesses can be "interleaved")
- Each Dimm can be dual rank - like two modules (why motherboards have groups of 2, 4, 6, 8 RAM slots)
