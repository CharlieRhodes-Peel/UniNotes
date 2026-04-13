# The Java Virtual Machine
Allows [[Java]] code to run on any machine - Creates a machine inside another, a "virtual" machine. It has it's ***own*** architecture & [[Instruction Set]] but it's **all** **software**
# Architecture:
		![[Pasted image 20240521142347.png]]
- There is ***ONE*** **[[heap]]** & ***ONE*** Method area per JVM
##### [[Threads]]:
- **Each** ***thread*** use an ***instance*** of the **runtime** **execution** **engine** to run code
- Each thread's **local** **memory** is made up of the **program** **counter** & **stack**
##### Java Stack:
- [[Java]] uses ***Stacks*** instead of [[Register]]s for it's ***temporary*** storage
- Each stack (used per thread) has a **program** **counter** which holds the [[Address]] of the next ***bytecode*** instruction to execute
	- Instructions pushed onto **stack** and results need to be **popped** off
- The stack holds state information for that thread (this it coordinates too)
- Deals with nested method calls (recursion n the like)
- They can store ***stack*** ***frames***
- The stack is an **Operand** **stack**
##### Stack Frame:
Like a frame for the space the stack might need, calculated at compile time.
Used on method calls, acts as a frame for that method's stack, contains:
- Space for **local** **variables**
- Space for parameters
- Space needed for frame data
- Space needed for intermediate computation
###### Storing local variables:
- Within a ***stack*** ***frame*** as an **ARRAY** of words
- Entries in array are **primitives** or **pointers** to things in **[[heap]]**

##### Method Area:
The Method area is used for ***class*** information (& [[Static Variables]] stuff (they are kind of the same thing though)), the ***class* *loader*** streams bytecode of the class files
- Method tables used for faster look up
- [[Threads]] all get access to this method table
###### Class Loader:
- Type info is extracted & put in the method Area (like int & stuff)
- Which is then **shared** by **ALL** ***[[threads]]***

##### [[Heap]]:
- **Object** ***instances*** are stored here
- $\therefore$ **NON**-**static** info is stored the [[heap]]
# Calling a Method A Walkthrough:
- Bytecode is created at compile time
- A thread makes the **execution** **engine** run this bytecode and each thread has a  **program** **counter** that points the next instruction.
- Each instruction is pushed onto the stack and their results are popped off
- If the instruction is a **method** **call** then a new **stack** **frame** is to be pushed onto the **stack** which contains the data needed to execute the method including it's own stack ! (look at stack frame space list)
- Once the method is executed it's stack frame is popped off the stack (which includes the method)