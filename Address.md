# Summary
- Addresses are a general-purpose interface
# Location of Data
- Physical addresses = actual location in [[RAM]] or main memory
	-  Contains:
		- Frame number (see [[Paging]])
		- Page offset
- Logical addresses = relative to beginning of program
	- Contains: (pages coved in [[Paging]])
		- Page number
		- Page offset
The two are reconciled at execution.
Which is what **base displacement addressing** is for


# Logical - Physical address mapping
If pages are $2^k$ words in size, mapping is very straight forward!
![[Pasted image 20231214161033.png]]

Physical address = frame number + page offset 
- Where:
	- frame number = when [[RAM]] is split into frames (see [[Paging]])
	- page offset = where in the page are you going to access (he explained it weird)