A heap is a ***complete*** [[Tree]] - Every level above lowest is full
MinHeap = Each child is greater than or equal to it's parent
MaxHeap = Each child is less than or equal to it's parent

In a min heap the minimum value is always the root

# Methods:
- Add(int elem);
	- Adds and element into a heap and ***percolates*** if need be
	- Worst [[Time Complexity]]: $\Theta$(log n)
	- Best [[Time Complexity]]: $\Theta$(1)
- RemoveMin();
	- Pop value out from root
	- Replaces it will the ***LAST*** element
	- Swap with the smaller child
	- Keep percolating this element down the heap
	- Worst [[Time Complexity]]: $\Theta$(log n)
	- Best [[Time Complexity]]: $\Theta$(1)

# How to represent in Array:
- Index starts at 1 to make math easier
- Index of 1 is the root of the [[tree]]
- Say a node has index i
	- It's children are at index's: (i $\times$ 2) & (i $\times$ 2 + 1)

# Common Uses!
#### Priority Queues: 
Heaps are a great data structure to use for priority queues as elements can be added to the heap in order of priority and RemoveMin() acts as a dequeue() method

### Heap Sort:
Put stuff into heap and then remove from said heap
Needs $\Theta$(n) additional memory
Worst case [[Time Complexity]]: $\Theta$(nlog n)
