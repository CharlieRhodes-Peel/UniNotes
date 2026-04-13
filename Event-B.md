- A Formal modelling language "A blueprint for code" that uses sets
# Variables
- Just any old variables, their value must be within the set that they are defines in tho
# Invariants
- Specify the properties that the variables **MUST** abide too (rules for the variables)
# Events:
- Like method, they specify how variable can be changed
	- This happens in the **actions** part of the event
- Events have guards which guard the event from the wrong variable state from accessing it
	- For example you cannot remove a variable from a set if the set is empty
- Initialisation is a special **unconditional** event
	- Only happens only **ONCE** and before every other event occurs
	- Initialises the machine's variables to values that establishes the invariants

# Notation Examples:
- How to set up a machine
	![[Pasted image 20240717195153.png]]
- Set membership
	![[Pasted image 20240717195336.png]]
- Adding money to a bank
	![[Pasted image 20240717200251.png]]

