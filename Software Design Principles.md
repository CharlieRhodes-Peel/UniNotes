- Software that cannot be maintained will be thrown away
# Duplication:
Reusing code
# Coupling:
- Links between separate units of a program
- If two classes depend closely on many details of each other } *tightly coupled*
**AIM** for **LOOSE** coupling: 
- Understand one class without reading others
- change one class without affecting others
- Thus: improves maintainability
- Does: decrease performance at the price for maintainability
# Cohesion:
- No. and diversity of tasks that a single unit is responsible for
- If Each unit is responsible for one single logical task } *high cohesion*
- Applies to classes and methods
**AIM** for **HIGH** cohesion !
- Understand what a class or method does
- Use descriptive names
- Reuse classes or methods
# Responsibility-driven design:
Q: Where to add a new method (which class)?
- Each class should be responsible for manipulating its own data ([[Encapsulation]])
- The class that owns the data should be responsible for processing it
# Refactoring:
- Classes are maintained, often code is added
- When refactoring code, separate the refactoring from making other changes
- Frist: Do refactoring only!!! (no changes allows)
- Test before and after refactoring to ensure that nothing is broken

# Design Questions:
- How long should a class be?
	- If a class does more than one logical entity, too complex
- How long should a method be? 
	- **ONE LOGICAL TASK**

### Further: 
[[Software Design Patterns]]