Architecture is an Instruction Set Architecture (ISA) + Machine organisation (Micro architecture)

### Instructions:
Instruction = Opcode + Operand(s)
MIPS is used to illustrate a classic RISC ISA. Instructions have 3 main type: R, I, J
![[Pasted image 20260216155859.png]]

### MIPS architecture
- Is representative of most modern ISAs (except from x86!)
- 32 registers
- $0 (register index 0) is wired to constant 0, other are general-purpose
- "load-store" architecture:
	- i.e most instruction involve registers only: Single-cycle
		- ```
			  add $1, $2, $3        # reg1 = reg2 + reg3
		  ```
	- special memory access instructions: possible multi-cycle
		- ```
			  lw $8 Astart($19)     # reg8 = M[Astart + reg19]
		  ```







### Examples:
##### ISA examples: 
- x86, ARM, MIPS, PowerPC, RISC-v, ...
##### Machine organisation:
- Bulldozer, Core-2, M1, M2

