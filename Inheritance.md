# Similar classes can be refactored to share a (separate) parent class
- There are also inheritance hierarchies
- uses "extends" in [[Java]]
- All classes inherit from the object class (done by default)
- Final stops overriding

		// way of using inheritance in practise
		parent

# Rules:
- Subclass constructors must always contain a 'super' call
- If none is written, the compiler acts as if there is an empty constructor from the parent class (superclass), only works if a superclass has a defined constructor with no parameters, otherwise does default (nothing)
- Must be the first statement in the subclass constructor

UML is good for class diagrams

# Example
- Methods in *Object* are inherited by **all** classes
	- Any of the methods may be overridden
- The *-toString* method is commonly overridden:
	- **public String toString()**
	- Returns a string representation of the object, so is usually changed to make the string the object returns more understandable to the user/programmer