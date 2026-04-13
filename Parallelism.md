Doing things at the same time!
# The Good Side of Parallelism
Data sharing is a huge benefit! That is, splitting a task up into multiple different jobs that can be completed together to reach a shared result.
When you can split up tasks evenly and [[Cache]] blocks are clean between [[Threads]]
#### An aside: More scalable solutions uses libraries
If wanting to create parallel code use libraries! They make it so so so so much easier
# The Bad Side of Parallelism
Problems start to arise with shared + read-write data
- Many cores can access a memory location
- Many cores can read and modify a memory location
## An example issue: Counters
```(*data) += 1;``` this code will result in multiple instructions, even if read as one instructions (like in X86) will execute will execute in multiple instructions
```
int curr = *data;
int next = curr+1;
*data = next;
```
## Possible Solutions
Best solutions is at the **SOFTWARE LEVEL** using *mutex* locks within the *code* itself, this is best because its not tied to any architecture 

Solutions can be done at the language level. For example, Rust doesn't allow data sharing. C/C++ make data-races undefined behaviour, could also add libraries for constructs for locking (mutex locks and stuff)

Solutions can also be done at the [[ISA]] level. 
- Cache line lock+unlock instructions: which is used in embedded systems, because they are hard to use in software but easy to use from a hardware level (embedded system heaven!) (see [[Microcontroller]])
- Locked instructions: **MOST COMMON** because used in **x86** and [[CISC]]-style architectures
- Conditional stores: used in [[MIPS]]/ARM and [[RISC]]-style architectures.
- Transactional memory: Intel sort of support this (TSX); though it isn't common.
# [[Cache]]s and Parallelism
## Realistic Model
![[Pasted image 20260303140032.png]]
### How Do they Talk to each other?
For data that it between long temporal distances the [[CPU]]s communicate through memory, and short temporal distances communicate through [[Cache]]
## Coherency through locking
Multiple processors are connected through [[Cache]]s, and identical addresses may be found on multiple caches. How do we deal with this?
- Atomic operations expand to: lock, update and release.
	- 1 [[CPU]] "claims" an address and another other core/CPU containing information about that address must evict it.
	- So only the CPU that claims the address can access it
	- Once the CPU is done with it, it them releases it. All core agree on **ONE** [[CPU]] that has the lock
### Problems with this:
**Lock contention** is really bad for performance obviously because each [[CPU]] is fighting to lock the same location. *eventually* progress will be made but bring overall progress back down to single-threaded, if not worse

**Cache thrashing**: Locking a variable evicts entire cache line
- Memory traffic even if conflicts don't occur
- Still need to move data from [[Cache]] to [[Cache]]

#### How to reduce these problems
The locks or **atomic operations** should be a very small percentage of the code because can massively reduce the speed of the code



#### "Traditional" [[Cache]]s makes single-threaded code faster
- [[Locality Principles]]
- Resource sharing: use Icache and Dcache over one memory [[bus]]
- Intra-core coherency: always read the last value written to address
#### Multi-core systems present opportunities and problems 
- Inter-core coherency: Each address must have a unique value
- Inter-core consistency: Is the history of operations consistent?