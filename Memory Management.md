**In D[[RAM]]** (main memory)
- Allocate memory to programs
- Manage [[virtual memory]]
- Protect against malware

## Memory Protection
- To protect the [[Operating Systems]]
- To protect programs from one another

## Translation lookaside buffer:
**[[Cache]] for the page tables**
- Every logical memory access can require **TWO** physical accesses:
	- Page table entry
	- Data
### Demand paging:
![[Pasted image 20231214162751.png]]
(This is similar to [[cache]] hits and misses in [[Cache]])
- TLB hit = Page is in [[Cache]]
- TLB miss = Find in [[RAM]] (if there) (and follow all previous steps)
- Page fault = If page not in [[RAM]] put in [[RAM]] (and follow all previous steps)
- Frame eviction = If [[RAM]] full ! swap a victim frame out and swap in desired page
	- This **IS** how [[Virtual Memory]] works
## Swapping:
**Move some data out to the hard drive, and free some area in the memory to do it**
- [[Operating Systems]] stores a queue of processes wanting to execute
	- Processes on the disk, queue in the kernel
- As space become available, the processes are loaded
- When a process finishes, it is removed
- A process may also be **swapped out** if it is **stalled** (waiting for I/O for example)
![[Pasted image 20231214155300.png]]
## Partitioning:
**Splitting the data up into different parts
- Fixed size memory partitions
	- 'Typical' usage implies a logarithmic distribution of partition sizes is best
	- Easy to administer
- Variable size memory partitions
	- Memory is allocated as required
	- Fragmentation makes it harder to load incoming processes
![[Pasted image 20231214155540.png]]

## [[Paging]]
## [[Virtual Memory]]