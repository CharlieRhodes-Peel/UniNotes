In [[Java]] The main way to ***create*** threads is to use the ***runnable*** interface
- To do this: Must override the **run()** method:

		//Example
		public class RunnableClass implements Runnable{
			@Override
			public void run(){
				System.out.println("I am running");
			}
		}
		public class main{
			public static void main(String[] args){
				RunnableClass runnableObj = new RunnableClass();
				Thread thread = new Thread(runnableObj, "Thread_Name1");
				thread.start();
			}
		}

# States:
There are 6 states a thread can be in, these being:
![[Pasted image 20240521152234.png]]
1. New - Start method has not been called yet
2. Runnable - Stuff RUNNING !!
3. Blocked - Acquiring a lock 
4. Waiting - for a notification
5. Time waiting - for notification or time is up
6. Terminated - Job is finished :)
# Priorities: 
- Each thread has a priority from 1-10: 
- These **DO** **NOT** *guarantee* they will be ran first, but it's like you're giving **hints** to the scheduler

		//Code:
		obj.setPriority(Thread.MIN_PRIORITY); // minimum priority

# Extra Stuff:
### 2 Main Threads:
- Main (calls all other threads)
- Garbage collection (collects and repurposes unused memory :)
### Daemon Threads:
- Low ***priority*** threads that run in the background
- They provide services to other threads -> like spell checking in word
- They will just stop if all other threads stop, [[JVM]] terminates
- Daemon threads can only create more daemon threads

### Thread methods:
You can also just check the api, actually yeah just do that i'm too lazy to list them:
https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html?ref=highscalability.com
