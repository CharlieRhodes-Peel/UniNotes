- Responders have an [[Address]] range
- Must select just one responder
	- Only one device at each address
	- Only one device drives data [[bus]]

# Diagram
- Chip select
	1 bit input to active responder
	Calculated as a function of address
	Instantiated by system integrator SW
- Address translation
	- Maps global address to local address
	- Usually just wires; may need adder
- Merge buses for read data
	- Can be as simple as "or"-ing wires
![[Pasted image 20260309143822.png]]



