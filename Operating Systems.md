- Goal is to hide complexity from programmers and users
### Concealing Complexity:
- Internet protocols
- Compilers
- Device drivers
- Run multiple programs at once

![[Memory Management]] 
# Task Management:
- Maintain list of running processes on the [[CPU]]
- Carry out timeslicing & context switching
- Handle interrupts (errors)
- Set program privilege levels 
- Launching programs
# File Management: - Non Volatile
- Open, read & close files
- Set & check permissions
- Handle buffering
# Device Management: 
- Device drivers for peripheries
	- Have open, read, write and close
# Others
- Context switching:
	- The state of a running [[Process]] is saved
	   and another [[Process]] given processor resources
- Timer:
	- Prevents job monopolisation
- Privileged [[instruction]]
	- Only executed by OS

# Idk where else to put
- 32 bit machines can only store up to 4 GB of data (only can [[address]] that much)
- 64 bit machines can [[address]] 16EB (like $2^{80}$)
- [[ROM]]