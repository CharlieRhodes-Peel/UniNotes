Shows the dynamic behaviour between elements and how they ***interact***
- Hence shows the **sequence** of events
There are two axis used in sequence diagrams -> is the elements in order of occurrence
and *down* is time
# Syntax:
## Element:
![[Pasted image 20240515145410.png]]
## Messages:
#### Synchronous:
- ***Requires*** a response before the interaction can continue
			![[Pasted image 20240515145510.png]]
#### Asynchronous:
- Doesn't require a response for interaction to continue
			![[Pasted image 20240515145606.png]]
#### Reply/Return:
- Return message back to the original lifeline
			![[Pasted image 20240515145641.png]]
#### Found / Lost:
Found: The sender is unknown
Lost: The receiver is unknown
			![[Pasted image 20240515145800.png]]
#### Reflexive:
- When an objects sends a message to itself or has to call itself
			![[Pasted image 20240515145918.png]]

## Fragments:
#### Alt / Alternative:
- Used when a ***choice*** needs to be made between two or more message sequences
			![[Pasted image 20240515150202.png]]

#### Repetition / Loop:
- Self explanatory really 
			![[Pasted image 20240515150329.png]]
#### Par / Parallel:
- Used to represent a parallel execution of interactions:
			![[Pasted image 20240515150423.png]]
#### ref / interaction use:
- Uses / Calls ***another*** ***interaction***
- Used to simplify large and complex sequence diagrams
- Hides the area behind it
			![[Pasted image 20240515150535.png]]


# Examples:
#### ATM Example
![[Pasted image 20240515145949.png]]
#### Online Assignment example:
![[Pasted image 20240515150621.png]]
# Fork vs Stair:
##### Fork:
![[Pasted image 20240519151936.png]]
- Fork is more centralised
- Can easily reorganise operations with fork
- Fork easier to add new operations
##### Stair:
![[Pasted image 20240519151949.png]]
- Dynamic behaviour is distributed
- Each object delegates responsibility to other object
- Each object only knows the inputs of the previous and the outputs it has to give to the next
- Operations have a strong connections
- Operations will always be performed in the same order




