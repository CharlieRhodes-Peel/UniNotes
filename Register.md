**- A group of Flip Flops that can store multiple bits** (see [[RAM]], section Flip Flops for more information)
- Registers are commonly used as temporary storage in a processor (think [[CPU]] architecture)
	- They are faster and more convenient than main memory
	- More registers can speed up complex calculations

## A basic register:
![[Pasted image 20231005151133.png]]

# How many general purpose registers are needed in [[CPU]]?
- ~ 16 (found in i7's) (32 for [[MIPS]])
- Fewer registers = >memory references
- But they take up more silicon area on the processor


# Shift Register:
![[Pasted image 20231005162810.png]]
shifting left is /2 and shifting right is x2


# More registers are good?:
- If you have more registers you have:
	- Longer instructions
		- More bits to encode
	- More to save on context switch
	- Increases cost
	- Increases complexity
Modern [[ISA]]s abstract physical registers behind architectural/logical registers:
- Think [[virtual memory]] but at the register level !
- For example:
	- Zen 3 (AMD 7000) has 160 floating point registers and 192 int registers
	- They use register renaming