# Summary

Generally this page looks at **controllers** and **responders** also known at "master-slave" but we don't really call it that anymore
## Diagram
![[Pasted image 20231102223052.png]]
# Parallel data bus
- Width is a key determinant for a parallel bus
	- Determines maximum memory capacity
- (64 bit = 64 bus lines)
	- Usually [[CPU]]'s only use this many internally (hogs space on the motherboard otherwise)
# On a conventional bus there are
### Data Lines
### [[Address]] Lines
### Control Lines
- Memory R/W signal
- I/O Port R/W signal
- Transfer Acknowledgement
- Bus request/grant
- Interrupt request
- Clock signals
- Reset


# Bus based architectures
- **Controller**: A component that creates read and write requests to [[RAM]]
- **Responder**: A component that services read and write requests
- Some components can be both **Controllers** and **Responders**
- **Arbitration**: Allowing multiple **controllers** to access one **Responder**
- **Bridging**: Mapping between buses with different characteristics
# Types of Buses
## *Proprietary*: single-purpose for internal use
- Example: the [[Instruction]] and data memory interfaces from lectures
- Example: pinout of a [[RAM]] [[IP core]] in ASIC or FPGA
### Asynchronous ROM
1. [[CPU]] places [[Address]] on Bus
2. Some time passes...
3. [[RAM]] will place data on bus
### Asynchronous [[RAM]]
- You **must** know they **delay** of read and write
1. [[CPU]] initiates transaction:
	- Place [[Address]] on bus
	- and either write=1 -> writedata must be set | OR | read = 1
2. Sometime passes
3. Memory completes transaction | If read=1 -> readdata will be set
### Synchronous [[RAM]] with stall
This is what was used in the [[MIPS]] [[CPU]] built up in (see, [[Control Signals]], [[Cache]])
![[Pasted image 20260309142512.png]]
- Not all reads/write are immediate
- Sometimes [[RAM]] must stall [[CPU]]
- Stalls require clocks
	- [[CPU]] and [[RAM]] use the same clock
- Same as asynchronous (above), execept:
	- stall = 0 -> read/write is complete
	- stall = 1 -> at least one more cycle
(see [[Stalling]])
- See [[Memory Mapping]]
## *Lightweight*: standardised buses for low-performance and low-area
### Avalon
Used by AMD for their lower-performance systems
Aka. NOT alot of CPUs, small bus widths, small responders and controllers etc.
- Clock-synchronous
	- Transaction starts in one cycle
	- It completes in the following cycle;
	- *or* wait request delays by one cycle (stall signal)
- Provides flexibility to responders
	1. Hold wait-request high
	2. Use wait-request for back-pressure
	3. Hold wait-request low
#### Diagram
![[Pasted image 20260309145225.png]]

## -> [[High-Performance Buses]] <-
# Arbitration
- Multiple controllers may need to access one responder
- A given responder can only service one controller at a time
- How do we manage access? what if we have two controllers for one responder?
	- Deterministic: grant accesses on a schedule (queue)
	- Priority based: one controller has priority over other controllers
	- Dynamic: grant access based on who requested it first
- Arbiration can get very expensive in space and time, even though they scale logarithmically, still increases
- Doing anything combinatorially at high clock rates is very difficult
## Diagram
![[Pasted image 20260309144615.png]]

