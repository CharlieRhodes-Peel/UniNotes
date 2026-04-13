Do while is laid out as such:

	do {
		//code
	} while (condition);
	//rest of code

condition is only checked at the end, the do code will always run

## For each loops:
For each loop is a shortcut for iterating through arrays in [[Java]]
Can only be used for **access** as it uses a **copy** of the array

	for (type variableName  : collection){
		System.out.println("Number is " + variableName)
	}
(collection is the array/list)