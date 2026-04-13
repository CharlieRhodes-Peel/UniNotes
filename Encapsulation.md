#### Prevents direct access from external classes
- Private everything !
	- Getting and setters aren't obv
- Programming practise to protect methods and ensure that inputs and outputs for methods are well defined (makes your code safer)
	- It is less fun tho
## Keywords:
Remember be paranoid ! Only change something from private if needed somewhere else !
- Public
	- Everyone can see it
- Protected
	- Only *this* class, it's *sub-classes* and the *package* can see it
- Default (no keyword)
	- Only *this* class and the *package* can see
- Private
	- Only *this class*
## Getters and setters
- Good programming practise (you should really use them more >:{ )
	- Allows for input and output validation (within the getters and setters)

# Benefits:
**Cleaner, Reusable, Maintainable code**
- It's the classes responsibility to manage itself
- Clean interface for outside world 
- Does not reveal inner workings
	- Less thinking required later !