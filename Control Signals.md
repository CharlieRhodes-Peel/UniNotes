---
aliases:
  - CPU design
  - Circuit Diagram
  - MUXes
---
# Summary:
- [[Control Signals]] What calculations *should* be done in *this* cycle
- [[Data Paths]]: What calculations *can* be done in *any* cycle

So far everything covered here is:
- Single-cycle: every instruction happens in one-cycle
- In-order: instructions executed in program order
- Clock-synchronous: every stateful component uses same clock
- Memory reads are combinatorial (any instruction / data reads **must** complete in **0** cycles) 
see, [[CPU Design Optimisations]] for how these things affect speed and how to optimise it

(see [[Assembly Shorthand]] for shorthand descriptions for below)

| Signal name | Effect when off (0)                                                                                          | Effect when on (1)                                                                                        |
| ----------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| MemRead     | None, e.g R, sw, beq                                                                                         | Data memory contents at the read address are put on the read data output e.g lw                           |
| MemWrite    | None e.g R, lw, beq                                                                                          | Data memory contents at address given by write address is replaced by value on write data input e.g sw    |
| ALUSrc      | The second [[ALU]] operand comes from the second register file output e.g R, beq                             | The second ALU operand is the [[Sign Extension]] of the lower 16-bits of the instruction e.g lw, sw       |
| RegDst      | The register destination number for the write register comes from the rt field e.g lw                        | The register destination number for the write register comes from the rd field e.g R                      |
| RegWrite    | None e.g sw, beq                                                                                             | The register on the write register input is written into with the value on the write data input e.g R, lw |
| PCSrc       | The PC is replaced by the output of the adder that computes the value of PC+4 (e.g goes to next instruction) | The PC is replaced by the output of the adder that computes the branch target (e.g goes to branch target) |
| MemtoReg    | The value fed to the register write data input comes from the [[ALU]] e.g R                                  | The value fed to the register write data input comes from data memory e.g lw                              |
| Branch      | 0 e.g R, lw, sw                                                                                              | 1 e.g beq                                                                                                 |
# Control Unit:
### For single-cycle datapath
Essentially can just use the above summary table to create a **LOOKUP-TABLE** of what type of instructions correspond to what type of control signal values
Simply: **OPCODE** IN -> **CONTROL** **SIGNALS** OUT
Often shown as a disconnected piece as can look really messy otherwise
##### Example:
lw instruction: lw 1010110
- MemRead = 1
- MemWrite = 0
- ALUSrc = 1
- RegDst = 0
- RegWrite = 1
- MemtoReg = 1
- Branch = 0
# Control Signals:
- Adding to the diagram given in the Summary of [[Data Paths]] we can add the following flags
![[Pasted image 20260217151724.png]]
- Reason RegRead does not exist is because you might as well just read the output and ignore the value if not needed
- This is not the case for memory because memory is "outside" of the [[CPU]] and in some cases (peripherals) reading from memory can change a value at that [[Address]]
- For issues with this design see [[CPU Design Optimisations]]

## Types of control flags
### [[ALU]] control part:
- ALUOp #*selects which operation [[ALU]] is doing*

Diagram shows that the **type** of [[ALU]] control can come from either the **function code** (opcode from i-type instruction, see [[MIPS]]) or from the **control unit** (r-type instructions, because opcode is always 0, see [[MIPS]])
![[Pasted image 20260217155710.png|300]]
### MUXes:
Generally these are in place to just flip between the multiplexers added in [[Data Paths]] for different instruction types
- RegDst #*selects the correct register index*
- ALUSrc #*controlling between r-type and memory instructions*
	- [[ALU]] always needs two values to operate on. first one always comes from register (see control signals section diagram) but second one can depend on the type of instruction
	- If not an R-type instruction then operand comes from the **immediate field** of the instruction (think of a register offset)
- MemtoReg #*controlling if memory writes to register*
- PCSrc #*controlling if branch (pos given from [[ALU]]) is taken*

### Storage:
- RegWrite #*should the register write given register*
*No need for RegRead because doesn't change state, can just ignore it if not needed*
- MemRead #*Needed on memory because some programs (peripherals) could change values on a read*
- MemWrite #*Should Memory Get written too this cycle?*

