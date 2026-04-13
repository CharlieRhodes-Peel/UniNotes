---
aliases:
  - CPU design
  - Circuit Diagram
---
# Summary
- [[Data Paths]]: What calculations *can* be done in *any* cycle
- [[Control Signals]] What calculations *should* be done in *this* cycle
![[Pasted image 20260216173042.png]]
# Data-path & control:
The following sections will build up to a derivation of the bottom diagram
![[Pasted image 20260216165518.png]]
### [[Register]]-based [[Instruction]]s
- Select read/write [[Register]]s from operands
- Select [[ALU]] operation from opcode and function code
```
  add $5, $6, $7 #reg[5] = reg[6] + reg[7]
``` 
- ![[Pasted image 20260216170103.png]]
- Where in the above image, the **Registers** blocks contains the current values of all 32 registers
### Memory access instructions: Load
```
lw $5, offset($6) #reg[5] = M[reg{6] + offset]
```
Assume data memory to return value in same cycle
![[Pasted image 20260216170656.png]]
See [[Sign Extension]] for more details on sign extend

### Combining datapath for R-type and memory instructions
![[Pasted image 20260216172121.png]]
Where MUX (multiplexers) flips between on and off (r-type or memory address) depending on the instruction type

### Adding Branch instructions
```
beq $5 $6, L # Branch if equal (reg[5] == reg[6] then jump to L)
```
![[Pasted image 20260216172419.png]]
- The shift left 2 is there to "get the most out of the bits you have" i.e you can only branch to the start of an instruction. Each instruction is a multiple of 4 (32). So the reason it's shifted is because the two least significant bits are going to be zero so you might as well not include them so that you can increase the distance you can jump the program counter by a multiple of 4
- The reason it goes to an add is because it is added to the program counter
### With instruction memory
![[Pasted image 20260216173042.png]]
PC+4 is the immediately following instruction because instructions are 4 bytes long in [[MIPS]]