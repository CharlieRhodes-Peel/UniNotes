# Summary:
![[Pasted image 20231213170605.png]]
- Each memory location mapped to *one* [[cache]] location
- Blocks of [[cache]] are allocated to certain addresses
- Most caches now are [[Associative Cache]]
For more information on [[Cache]]s generally, see [[Cache]]
# Composition of a [[Cache]] Block
![[Pasted image 20260224123720.png]]
Where:
- Index = [[Cache]] index
- Valid = Stores a check if [[cache]] entry is valid
	- Is done this way so e.g when PC boots can set all valid to 0
- Tag = Stores a check if [[cache]] entry = required item
## Sizing of [[Cache]]:
- Byte = Smallest **addressable** unit of memory (8 bits)
- Word size w >= 1, in bytes
	- Natural granularity of [[CPU]], size of [[Register]]s
- Block size k >= 1, in words
	- Granularity of [[cache]]-to-memory transfers
- [[Cache]] size c >= k, in words
	- Total size of [[cache]] storage, No. blocks is (c div k)
```
1. word_address = (byte_address div w);
2. block_address = (word_address div k);
3. block_index = (block_address mod (c div k));
```
# Lookup Algorithm:
![[Pasted image 20260224125605.png|500]]
In the above diagram the top bar represents some address in memory with the [[Cache]] the *table*/*excel spreadsheet* looking thing
- The part that is 10 bits long gives the exact position of what it is in [[cache]] (the **index**)
- Then the **Tag** is checked against the [[Cache]] tag, if they are equal (and block is valid) then [[Cache]] HIT!
# Handling Misses
## By exception + stall:
- [[Cache]] miss on instruction read:
	- Restore PC (program counter) (decode twice)
	- Send address to Main Memory ([[RAM]]) and wait (**stall**) 
	- Write data received from memory to [[Cache]]
	- Re-fetch instruction (from restored PC)
- [[Cache]] miss on data read:
- Similar: **Stall** [[CPU]] until data from main memory ([[RAM]]) is available in [[Cache]]

# Dirty [[Cache]]
When a *block* is changed in [[Cache]] it *won't* have propagated to *memory* yet. We make sure that memory stays up-to-date s.t:

- When a *block* is *modified* in [[Cache]], it is marked as **dirty**
- When a block is **dirty**, it means that when it's about to be overwritten, the [[CPU]] first checks the dirty **bit** and if is marked as dirty, writes back to main memory
	- It's actually placed on the **WRITE BUFFER** (see [[Direct Mapped Cache]] for more info)

# Extension of design:
[[Multi-Word Blocks]] - Builds on this design, adding multiple words per block

