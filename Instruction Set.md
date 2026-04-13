- A list of all possible [[Instruction]]s that a processor can run
- 1 Assembly Code Instruction = 1 Machine Code Instruction
# ISA vs architecture
- The [[ISA]] is a contract
	- Anything specified by the [[ISA]] must be implemented by all architectures
	- Anything not specified by the [[ISA]] is an architectural choice
- [[ISA]]s usually focus on *functional* aspects
	- Given a well defined instruction stream, is the output correct?
	- More recently: formal definition of ISA semantics
- Architectures usually focus on *non-functional* aspects
	- How "fast"?
	- How much area?
	- How much power?
	- Per-unit-cost?


# Microarchitectures can share [[instruction]] sets:
- e.g Intel [[Core]] [[CPU]] and AMD Ryzen share an instruction set
	- [[x86]]
	- ARM (used on Raspberry PI)
# Examples of Instructions Sets:
- [[MIPS]]
- x86
- ARM
- PowerPC
- RISC-V
- ...