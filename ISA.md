# [[Instruction Set]] Architecture: 
## Which one is best?:
- If [[RISC]]-based ISAs give better performance-per-way than [[CISC]], why did [[x86]] (a [[CISC]] architecture) dominate (on desktops)
## **Main types**:
#### Accumulator based 
**Properties**:
- Short Instructions
- One implicit operand, one explicit
- **Single** temporary storage location :(
	- High memory traffic

X = A + B is:
- LOAD A
- ADD B
- STORE X
#### Stack based (common in 1960s):
**Properties**:
- Simple Model
- Short Instructions
- Implicit operands
- Stack cannot be randomly accessed
	- Can become a bottleneck

X = A + B is:
- PUSH A
- PUSH B
- ADD
- POP X
#### Register-memory based:
- Intel [[x86]], IBM 360/370
**Properties:**
- Easy code generation (very explicit)
- Clever compiler optimisations
- Fast access to temporary values
- Operands and instructions will have to contain more bits

X = A + B is:
- LOAD R3, A
- ADD R1, R3, B (Result Register, Other Value Location, B)
- STORE R1, X 

#### Register-register (load/store):
- ARM, [[RISC]]-V, Alpha SPARC
**Properties:**
- Fixed-size instructions
	- Simple encoding
- Simple code generation (also very explicit)
- (most) Instructions require a similar known number of cycles
- Fast
- High instruction count
X = A + B is:
- LOAD R3, A
- LOAD R2, B
- ADD R1, R3, R2
- STORE R1, X

#### Memory-Memory (not used today):
Reading and doing instructions all on memory (very slow!)
- Produces compact code
- Large variation in:
	- Instruction size
	- Execution time per instruction
- $\therefore$ memory access is the bottleneck


