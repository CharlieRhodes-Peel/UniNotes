awArchitecture is an [[Instruction Set]] Architecture (ISA) + Machine organisation (Micro architecture)

# Instructions:
[[Instruction]] = Opcode + Operand(s)
MIPS is used to illustrate a classic RISC ISA. Instructions have 3 main type: R, I, J but they are all a fixed size of 32 bits long
![[Pasted image 20260216155859.png]]
### R-type = Register
![[Pasted image 20260216161211.png]]
- Used for: Arithmetic, comparison, logical operations, stuff like that
	```add $8, $17, $18 #reg8 = reg17 + reg18```
- MIPS assembly: *Destination* is usually given **FIRST**
- Opcode is **ALWAYS** zero
### I-type = Immediate
![[Pasted image 20260216162410.png]]
The operands being immediately available as part of the instruction itself. What does this mean? It means it is used as part of:
- Memory access (load and store instructions)
- Conditional Branches
- Arithmetic with constants
	- ```add $1, $2, 100 #reg1 = reg2 + 100```
### J-type = Jump
![[Pasted image 20260216162751.png]]
Used for unconditional jumps (branches) and is good at jumping a long distance (e.g function calls from system libraries)
**NOTE**: other *jump* instructions can be I-type or R-type! (shorter distance)
```
j 1236 # Jump to instruction at address 1236
jal 1236 # Save address of next instruction in register $31 before jumping to             # 1236
```
# MIPS architecture
- Is representative of most modern ISAs (except from x86!)
- 32 [[Register]]s
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


# Example:
![[Pasted image 20260216164005.png]]

# [[Pipelining]]:
- Five stages, one step per stage, each stage takes one clock-cycle
1. IF: Instruction **F**etch from memory 
2. ID: Instruction **D**ecode & register read
3. EX: **Ex**ecute operation or calculate address
4. MEM: Access **Mem**ory operand
5. WB: **W**rite result **B**ack to register