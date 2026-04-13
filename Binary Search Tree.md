# Definition:
A [[Tree]] that follows these rules:
1. Each element in the **left** subtree is **less** than the root element
2. Each element in the **right** subtree is **more** than the root element
3. Both left & right subtrees are also **Binary** **Search** **Trees**

# Searching (for value t in tree):
0. Start at root
1. Compare value to t
	1. If **t** is **smaller** **than** the **value** then go **left**
	2. If **t** is **larger** **than** the **value** then go **right**
	3. If **t** **IS** the **value** then **stop**
- The **fuller** the tree the **quicker** the search

# In-order Tree walk:
- Prints all elements in binary search tree in order
- Simple **recursive** **depth first** [[algorithm]]

		//Tree Walk Function
		void printTree(Node n){
		 if(n != null){
			printTree(n.left)
			print(n)
			printTree(n.right)
		 }
		}

# Notes:
- A binary search tree can be a good implementation of a [[set]]
- Trees have iterators that allow them to be walked through in order
### [[Time Complexity]]:
- Worst Case Search: $\Theta(n)$
- Best Case Search: $\Theta(1)$
- Average Case Search: $\Theta(log(n))$ (if tree is balanced)