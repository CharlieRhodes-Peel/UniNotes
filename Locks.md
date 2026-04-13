Locks in [[Java]] Stop [[Threads]] from becoming ***Deadlocked***!
# Function:
Locks ensure that only **one** thread can access a shared resource (eg. variable, methods or blocks of code) at a given time.
If a thread is accessing this resource no other thread can access it as the shared resource becomes ***locked*** the lock is relieved when the thread is finished.
# Implementation in [[Java]]:
#### Synchronisation:
The "***synchronized***" keyword can be used to mark blocks of code or methods.
This means that once a thread is accessing this block of code all other threads are locked until the thread inside is done

When done on the code block, the lock is only on the lock object

	// Code block example
	Object lock = new Object();#
	
	synchronized (lock){
		//code goes here
	}

	// Method example
	public synchronized void someMethod(){
		//code goes here
	}

# Where they are useful:
- Ensuring thread safety when accessing a shared resource
- Preventing data from concurrent modification
- Implementing the producer and consumer [[Software Design Patterns]] (factory)