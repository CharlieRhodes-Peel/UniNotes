# Big O Notation
- Only care about **WORST** case, Therefore if an [[algorithm]] is O(n$^2$) the time complexity will **NOT** be worse than that

# Big $\Omega$ Notation:
- Is the **LOWER** bound, so if something is $\Omega$(n) the [[algorithm]] is **NO** **LOWER** than that.
- Useful for analysing **BEST CASE** of an [[algorithm]], can show how fast the [[algorithm]] can be at it's best case
- Example: Linear search [[algorithm]], When searching through an array linearly the best case is the target item is the first item checked $\therefore \Omega(1)$.
- Example: Merge sort - Has a time complexity of O(n log n) However the best case is when the array is already sorted in which the merge sort runs in $\Omega(n)$ taking a linear amount of time in the **BEST** **CASE**
# Big $\Theta$ Notation:
- Combines Big O and Big $\Omega$ Notation by being able to do both, it can act as an upper or lower bound for a [[algorithm]].
- Useful when analysing **AVERAGE** case
- When an [[algorithm]] is said to be say $\Theta$(n log n) that means there exist **POSITIVE** **constants** $c_1$ and $c_2$ such that:
	 $c_1 \cdot n(log(n)) < T(n) < c_2 \cdot n(log(n))$
	 where $T(n)$ is the time complexity of the [[algorithm]] with input n.
- Meaning that the time complexity is **BOUNDED** both above and below by constant values around the $\Theta$ stated.
# Examples: 
- Linear Search [[Algorithm]]: O(n) | $\Omega$(1) | $\Theta(1)$ (theta for best case)
- Merge Sort: O(n log n) | $\Omega$(n) | $\Theta$(n log n) (theta for average and worst case)

