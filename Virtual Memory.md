# Allows more processes in [[RAM]] !!
- **Pages** ([[Paging]]) swap in and out as required
- A single [[Process]] offset is no longer enough
- We **need** as **TABLE** of offsets for ***each*** page
	- Creating a ***page table***
- Logical [[Address]]es now refer to a page, the page table translates the base address (logical page) to the physical [[Address]] (physical frame) (see [[Memory Management]])
![[Pasted image 20231214160818.png]]

How it works (also in [[Memory Management]])
![[Pasted image 20231214163147.png]]