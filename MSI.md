**M**odified, **S**hared, **I**nvalid
# Summary
A way of reaching [[Cache]] coherency, defining different states that a [[Cache]] block can be in. It is generally better than having atomic operations with [[Cache]].

Each [[Cache]] block in each [[CPU]] [[Cache]] has one state:
- **MODIFIED**: the block is dirty:
	- Eventually this block must be written back to [[RAM]]
	- No other [[CPU]]s [[Cache]] is allowed to contain the same [[Address]]
- **SHARED** the block is clean:
	- The block can be discarded without writing back
	- Other [[CPU]]s may contain the same address (also marked as clean)
- **INVALID**: the block does not contain anything
# Pros and Cons
## Pros
It ensures coherency for any given address
Un-modified (shared) data can be used in parallel
It is simple to implement
## Cons
All traffic goes via the memory [[bus]]
- Must evict then re-read, even if data already in another cache
Notifications between all [[CPU]]s are costly
- Gets **MORE** expensive with more [[CPU]]s
# State Machine Design
## Diagram
None bold lines indicate when a state transition is orchestrated from another [[CPU]]/core
![[Pasted image 20260303143808.png|500]]
## State Transitions
##### INVALID -> SHARED
CPURd = CPU *load* instruction
BusRd = Read transaction over [[bus]]
##### INVALID -> MODIFIED
CPUWr = CPU *store* instruction
BusRdX = Read transaction over [[bus]] **and** take *exclusive* access
##### SHARED -> MODIFIED
CPUWr = CPU *store* instruction
BusUpgr = Tell other [[Cache]]s you're taking *exclusive* access
##### SHARED -> SHARED
CPURd = CPU *load* instruction
##### MODIFIED -> MODIFIED
CPURd = CPU *load* instruction
CPUWr = CPU *store* instruction

# Notifications between cores
#### Snooping: Each cache "listens" to every other [[Cache]]s accesses
- Full cross-bar $O(n^2)$ area; $O(log(n))$ time
- Ring: $O(n)$ area; $O(n)$ time
#### Directory: Shared data structure tracking cache locations
- E.g hash table on addresses, or linked-list through caches
- A single directory can become its own bottleneck
# Extensions: MESI & MOSI
## MESI: Adds an **Exclusive** state
- Exclusive lines are clean, but only in one cache
- **EXCLUSIVE -> MODIFIED**: If owning [[CPU]] writes to line
- **EXCLUSIVE -> SHARED**: If another another [[CPU]] tries to read it
- Allows transfer of clean data between [[Cache]]s
## MOSI: Adds an **Owned** State
- Owned lines are dirty, but can be read by other [[CPU]]s
- Avoids writing dirty lines back to memory
- Allow transfers of dirty data between caches