# Summary
Essentially it's storing **multiple words** within one block. It's an extension to the [[Direct Mapped Cache]] design of [[Cache]]. 

The reason is to help with **SPATIAL LOCALITY** (see [[Locality Principles]])
## Example
In the below example we have 4 words per block. Meaning we have an additional *block offset* defined in it's addressing as to identify which block we are talking about
![[Pasted image 20260225154138.png|1000]]

# Impact of block size on miss rate
- **Increased** *block* size = **Decreased** *miss* rate (generally)
	- For large blocks in a small [[Cache]]
		- **INCREASED MISS RATE** - too few blocks
- However, **Increased** *block* size = **Increased** *transfer* *time* between [[cache]] and main memory aka *miss penalty* goes up
![[Pasted image 20260225160934.png]]
# Composition of [[Cache]]
![[Pasted image 20260225154430.png|500]]
In older [[Instruction Set]]s such as [[MIPS]] Addressing a WORD that is unaligned (such as doing a lw from 1055) is **ILLEGAL**.In modern [[ISA]]s this can be allowed. Doing so however would need **two** accesses to [[RAM]] and such would need **two** clock **cycles**

# Handling Misses
## Write-back with write-allocate
Where every write fetches the information into [[cache]] first and then store in [[cache]].
### On Read (lw)
- Same way as explained in [[Direct Mapped Cache]]
- Bring back *entire* Multi-Word Block from Memory
### On Write (sw)
- First Checks [[Cache]]
	- If **HIT** then change in [[Cache]] and mark *block* as **dirty** (see [[Direct Mapped Cache]] for **dirty** block explanation)
	- If **MISS** then change **READ** from memory **INTO** [[Cache]] and then proceed as if *hit*
## Write-Back with no-write-allocate
Writes go straight to memory, misses don't fetch the block into [[Cache]]