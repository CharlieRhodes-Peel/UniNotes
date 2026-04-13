---
aliases:
  - Flynn's Taxonomy
  - SISD
  - MISD
---
# Summary
Clock speed over time graph (doubles every two years ?)
- However, has stagnated at the 2-3 GHz mark (can't go any faster !!)
	- Single-Thread perf has increase (we've made smarter use of the [[CPU]])
- As you increase clock speed, you increase the power (linearly)
	- Nowadays ~300W for one [[CPU]] (high end)
- So we **CAN'T** just increase clock speed forever
## Diagram
- ![[Pasted image 20231213150911.png]]
# Flynn's Taxonomy
![[Pasted image 20231213143950.png]]
### Single Instruction Single Data (SISD)
- Late 90's
- [[Microcontroller]] NO PARALLISATION
- What gets covered in simple [[CPU]] designs such as [[CPU Design Optimisations]], [[Data Paths]], [[Control Signals]]
### Multiple Instruction Single Data (MISD)
- Multiple instructions on the same data
- Basically [[Pipelining]] but can use [[RAM]] as a processor (what ??)

### -> [[SIMD]] <-

### Multiple Instruction Multiple Data -> [[MIMD]] <-
- [[Modern CPUs]] processor
#### Symmetric Multiprocessors - SMP
- Multiple [[CPU]]s (or cores) share main memory and I/O
- Hardware manages contention
	- Has to be handled by the [[Operating Systems]]
- Increases performance especially multiuser/thread
- Reasonable scalable until [[bus]] is saturated
###### Typical SMP System
- Each processor has it's own L1 and L2 [[Cache]] (some have L3 which are shared between cores)
	- Connected by a system [[Bus]], or other interconnect
	- Main memory, I/o, etc. All connected to the interconnect
![[Pasted image 20231213150458.png]]


# Extras
### To have "true parallelism" you need: 
 - Data parallelism: split the data to make independent parallel tasks
 - Task parallelism: split the code up - e.g. [[threads]] on separate [[CPU]]s

#### Specialised distributed computing:
Giving **your** processor power !
- Contributed cycles 
- Specialised code runs simulations on donated [[CPU]] time
	- Usually for medical research / climate models

