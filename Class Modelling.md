- Is a *specialized* type of modelling concerned with the general structure of the system
	- Defines: Structural & behavioural features
# Class Diagrams:
- Attribute syntax: *visibility* attribute_name : type = initial_value
	- *visibility* = {- private, + public, # protected}
## Associations:
Binary association:
- Read for left to right or in the order specified by a **SOLID** black **triangle**
             ![[Pasted image 20240515142155.png]]
 N-ary association:
 - Relates 3 or more classes together					
			 ![[Pasted image 20240515142413.png]]
Aggregation - Weak lifecycle dependency:
- Weak lifecycle dependency meaning the life of the left element does **NOT** **DEPEND** on the right element
- Every Aggregation is also an association
- Example: Life of the wheels does not **depend** on the car, the car **HAS** wheels
			![[Pasted image 20240515142813.png]]
Composition - Strong lifecycle dependency:
- Strong lifecycle dependency meaning the life of the left element **DEPENDS** on the right element
- Every Composition is also an aggregation and an association
- Example: A human contains a brain, a brain depends on the human to life and vice versa
			![[Pasted image 20240515143020.png]]
Generalisation:
- Receives attribute & relationships from more general element
- Example: A Toyota **IS** a car
			![[Pasted image 20240515143146.png]]
