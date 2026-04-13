# Summary
The problem with [[Direct Mapped Cache]] is that every memory block has exactly *one* place it can go in cache. This causes a problem called **conflict misses**. Two frequently used blocks might keep kicking each other out because they both map to the same cache, which is slow, even if other slots are empty!

[[Associative Cache]] solves this by giving blocks more flexibility in where they can live
## Performance
Generally doing associative caches and having large number of **sets** increases the **hit time** (see [[Cache]] or [[Direct Mapped Cache]]) but reduces the miss rate. Is generally faster than [[Direct Mapped Cache]] though, due to **temporal locality** (see [[Locality Principles]])

**Increasing** *associativity* **decreases** the *hit rate* but **reduces** the *miss rate*. So have to weigh up the trade off. 
# Different Type of Associativity
## Set Associative - Most Used
The cache is divided into **sets**, and a block maps to a specific set (like [[Direct Mapped Cache]]) but within that set it can go into any of several slots. So a **4-way** set associative cache for example has 4 slots to choose from. So on look up there is only 4 places to check

It's like 4 [[Direct Mapped Cache]]s working in parallel
### Example
![[Pasted image 20260225180751.png|600]]
## Fully Associative - Not Really Used
A block can go **ANYWHERE** in the cache. Maximum flexibility, however to find the block you have to check **EVERY** cache entry at once

# Block Replacement
When you have a conflict and you have to replace a block in [[Cache]]
## Random selection - Simplest
Just evict a random block
- Simplest to add into hardware
- Works best for large caches with large associativity
## Least Recently Used: LRU
Evict the least recently used block in a set
- Works best for small cache sizes and small associativity