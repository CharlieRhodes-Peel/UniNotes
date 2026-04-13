# AXI
- Decompose buses into channels
- Reading from memory
	- Read address channel: CPU -> RAM
	- Read data channel: RAM -> CPU
- Writing to memory
	- Write address channel: CPU -> RAM
	- Write data channel: CPU -> RAM
	- Write response channel RAM -> CPU 
- Each channel is independent
	- Uses ready+valid hand-shaking
- Read address channel
	- Gives next address to be read
	- Don't know when read will happen
#### Diagram:
![[Pasted image 20260309150027.png]]


# Adding pipeline registers
![[Pasted image 20260309182048.png]]
- Register slices inserted
- And now the critical path is not an issue as there are no longer combinatorial paths
- Most modern busses are pipelined | can queue and buffer as needed

# Additional Features
- Bridging: we can automatically bridge between cahnnels
	- Clock domains: FIFOs can be used to move between components on different clocks
	- Data widths: adapt data channels between wider/narrower data widths
- Pipelining: multiple memory transactions in-flight at once

# Crossing clock domains
- Chips don't have just one clock
- Crossing clock domains is tricky but careful bus design makes it easy
![[Pasted image 20260309182505.png]]
# Out of order
- Some requests are "faster"
	- Could be due to [[Cache]] or could map to different [[RAM]]s
- Each transaction is tagged
	- Unique ID for read request
	- Corresponding id for read data
- Controller manages tags
	- Tags are low bit-width
	- Eventually will be re-used but as long as two duplicates aren't in flight at the same time it's fine
# Bridging and Bursting
- Data-buses can be different widths
	- [[RAM]] often wider and lower clock
	- [[CPU]] narrower and faster clock
- Automatic bridges and adapt widths
	- e.g a parallel to serial shift register

1. Single read address for 128 bits
2. [[RAM]] : provides 128 bit result
3. CPU receives first 32 bits
4. CPU receives second 32 bits
5. and so on...

![[Pasted image 20260309183742.png]]