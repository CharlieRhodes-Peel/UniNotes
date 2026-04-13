# Summary:
- D[[RAM]], S[[RAM]] used where appropriate
- ~1ns Speed
- Caches are needed to speed up access to D[[RAM]]
	- Depend on local access
- Three level are currently used
	- L3 = multiple cores share a large cache
- 95% cache hits means less [[RAM]] access so it is much faster and multi-[[core]] access is efficient
- Code can take cache size into account for speed

![[Pasted image 20231213164918.png]]
- Diagram:
	- Cache: 32-64 bits wide ; 40 - 80 GiB/s
	- Main Memory: 64 bits wide ; 10 - 20 GiB/s

- Small block of fast Static [[RAM]] located **ON** a [[CPU]] chip
- Memory requests go there

### Terminology:
- Hit rate: Ratio of cache access to total memory access
- Hit time: Time to access cache + determine if hit/miss
- Miss penalty: Time to replace item in cache + time to transfer to [[CPU]]

# How it works:
1. [[CPU]] wants to read a memory location
2. [[Address]] goes to cache
3. If present:
	1. Cache hit, provides data
3. If not present:
	1. Read required block from main [[RAM]] to cache (Cache miss)
4. Deliver data requested by [[CPU]]
# Cache Performance:
- [[CPU]] time = (Execution cycles + Memory **stall** cycles) $\times$ Cycle time
- Total **stall** cycles = Read **stall** cycles + Write **stall** cycles
- Read **stall** cycles = (Reads / Program) $\times$ Read miss rate (%) $\times$ Read miss penalty (cycle)
- Write **stall** cycles = (Writes / Program) $\times$ Write miss rate (%) $\times$ Write miss penalty (cycle) + Write buffer **stalls** (when full)
## Effect on [[CPU]]
Let:

| Var | What it is                        |
| --- | --------------------------------- |
| c   | Cycles Per Instruction (no stall) |
| p   | Miss penalty                      |
| n   | Instruction count                 |
| i   | instruction miss rate (%)         |
| d   | data miss rate (%)                |
| f   | load/store freq.                  |
- Total memory stall cycles: nip + nfdp
- Total [[CPU]] cycles without stall: nc
- Total [[CPU]] cycles with stall: n(c + ip + fdp)
- % time stalled: (ip + fdp) / (c + ip + fdp)
# Cache Design:
- Mapping Function Needed - cache is smaller than [[RAM]]
- Replacement Algorithm
- Write Policy
- Block Size
- Number of Caches ([[Instruction]] Cache + Data Cache)
## Different Types of Cache Design:
- [[Direct Mapped Cache]] - with [[Multi-Word Blocks]] as an extension
	- Simple
	- Fast accesses
	- High miss rates
- [[Associative Cache]]
	- Fully associative - Each [[Address]] maps to (c div k) blocks
		- Low miss rates
		- Costly
		- Slow
	- n-way set associative: Each [[Address]] maps to $n$ blocks
		- Each set contains $n$ blocks; num of sets, s = (c div (n $\times$ k))
## Avoiding Cache misses:
- Align data to the cache line boundaries
- Try to access *consecutive* bytes in a cache line

# Cache write buffer:
**![[Pasted image 20260224131823.png]]**
- Where the write-buffer is a FIFO queue
	- Acts as a sort of '**energy battery**' where it *smooths out* write bursts
## Cache Write Policy:
- Need to maintain **cache coherency**
	- How do we maintain agreement between cache and memory?
- **Write back**: Write to cache only
	- Complex control, need '*dirty*' bit for cache entries
	- Have to flush *dirty* entries when they are evicted
- **Write through**: Write to both cache and memory:
	- Memory write bandwidth can cause bottleneck
	- A big part of caches is to reduce this apparent bandwidth
	- Solution to this problem? Add more levels, similar to Level-2 Cache (see multi-level cache below)
# Multi-level caches:
## 2 Level caches:
- Big caches have longer latency so generally use smaller L1 then bigger L2 cache:
![[Pasted image 20231213170117.png]]
## 3 Level caches:
- L3 caches shared by multiple cores
	- Used to "shield" [[RAM]] from the cores
(Skylake design) ![[Pasted image 20231213170339.png]]
## With multiple Cores:
Multiple Cores may share the same L2 cache which then may share l3 at a higher level. Think of it as a hierarchy in terms of what each core can access
### Diagram
![[Pasted image 20260225182725.png]]
