- Fixed and variable size partitions are very inefficient
- Divide the physical memory ([[RAM]]) into lots of small, **EQUAL** chunks (frames)
- Divide the process into chunks (pages) of the same size as memory frames
- The process of mapping pages -> frames is efficient (in terms of memory)
![[Pasted image 20231214160336.png]]

# Page Tables:
- Hold all the pages of a process
- Can be:
	- Multi-level page table hierarchy
	- Hash table
	- Other approaches (there are many)

