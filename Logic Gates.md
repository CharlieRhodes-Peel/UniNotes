# Notation:
### + = OR ![[Pasted image 20231004132657.png]]
### $\cdot$ = AND ![[Pasted image 20231004132642.png]]
### $\bar{A}$ = NOT (where $A$ is input) ![[Pasted image 20231004132713.png]]
### $\bigoplus$ = XOR ![[Pasted image 20231004132618.png]]

### It is useful to see AND as $\times$ & OR as +:
- A $\cdot$ 0 = 0
- A $\cdot$ 1 = A
- A $\cdot$ A = A
- A $\cdot \bar{A}$ = 0
- A + 0 = A
- A + 1 = 1
- A + A = A
- A + $\bar{A}$ = 1
# NAND:
- Can be seen as a **"Universal gate"**
	- Due to DeMorgan's Theorems ([[Boolean Algebra]]), a NAND gate can really do anything (build whole computers)
	- ![[Pasted image 20231004134608.png]]

# Tri-State:
- Either 1, 0 or OFF
	- Used on shared [[bus]] wires