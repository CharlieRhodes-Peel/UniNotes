Greek for "many shapes"
# What is considered polymorphism:
- Substitution
- Overriding
- Dynamic Binding

## Substitution:
Substitution is when the language finds the most specific (lowest down in class tree hierarchy) method from the methods within an [[Inheritance]] tree

	// Example code
	// CD and DVD inhert from items class, items contains method .print(), CD
	// contains .getNumberOfTracks() which is unqiue to that class
	// Doing:
	Items i = new CD("Nevermind", "Nirvana", 11, 56)
	i.print() //This WILL compile
	i.getNumberOfTracks() // This will NOT compile
- Will not compile because, [[java]] will forget if it's a CD or a DVD because stored in an item reference

## Overriding:
- When a superclass calls methods on those sub-classes if there are more specific methods defined
## Dynamic Binding:
- The call gets diverted at run-time to the most specific method (kinda just the method in which the compiler uses to work out with method to run when there is overriding)

- What happens when u want to do a method from the parent class?

		super.method_name(parameter)
- Cannot do super.super(parameter) as a class **ONLY** knows **it's parent** class, not it's "grandparent" or "great grandparent" as that is kinda breaking [[Encapsulation]] a lil bit


