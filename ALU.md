# Summary:
- [[Control Signals]] What calculations *should* be done in *this* cycle
- [[Data Paths]]: What calculations *can* be done in *any* cycle

(see [[Assembly Shorthand]] for shorthand descriptions for below)

| Signal name | Effect when off                                                                  | Effect when on                                                                                         |
| ----------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| MemRead     | None, e.g R, sw, beq                                                             | Data memory contents at the read address are put on the read data output e.g lw                        |
| MemWrite    | None e.g R, lw, beq                                                              | Data memory contents at address given by write address is replaced by value on write data input e.g sw |
| ALUSrc      | The second [[ALU]] operand comes from the second register file output e.g R, beq | The second ALU operand is the [[Sign Extension]]-extend lower 16-bits of the instruction e.g lw, sw    |
|             |                                                                                  |                                                                                                        |
|             |                                                                                  |                                                                                                        |
|             |                                                                                  |                                                                                                        |

![[Pasted image 20260217160515.png]]
Where deasserted means off (0) and asserted means on (1)
# Control Signals:
- Adding to the diagram given in the Summary of [[Data Paths]] we can add the following flags
![[Pasted image 20260217151724.png]]
- Reason RegRead does not exist is because you might as well just read the output and ignore the value if not needed
- This is not the case for memory because memory is "outside" of the [[CPU]] and in some cases (peripherals) reading from memory can change a value at that [[Address]]

## Types of control flags
### [[ALU]] control part:
- ALUOp #*selects which operation [[ALU]] is doing*

Diagram shows that the **type** of [[ALU]] control can come from either the **function code** (opcode from i-type instruction, see [[MIPS]]) or from the **control unit** (r-type instructions, because opcode is always 0, see [[MIPS]])
![[Pasted image 20260217155710.png|300]]
### MUXes:
Generally these are in place to just flip between the multiplexers added in [[Data Paths]] for different instruction types
- RegDst #*selects the correct register index*
- ALUSrc #*controlling between r-type and memory instructions*
	- [[ALU]] always needs two values to operate on. first one always comes from register (see Summary in [[Data Paths]] for diagram) but second one can depend on the type of instruction
	- 
- MemtoReg #*controlling if memory writes to register*
- PCSrc #*controlling if branch (pos given from [[ALU]]) is taken*

### Storage:
- RegWrite #*should the register write given register*
*No need for RegRead because doesn't change state, can just ignore it if not needed*
- MemRead #*Needed on memory because some programs (peripherals) could change values on a read*
- MemWrite #*Should Memory Get written too this cycle?*

