An AVL tree is a [[Binary Search Tree]] that has a ***balance** **factor*** to keep it balanced.
Ensures the [[Time Complexity]] of search is at ***WORST*** $\Theta(log(n))$

# Definition: 
- It's a [[Binary Search Tree]]
- Left & Right subtree's height differ by **AT** **MOST** 1
- Every subtree is also an AVL tree

# Implementation:
- Each Node n has a balance factor bF
- Each Node also has the height h of it's subtree's: H(h) = max(H($h_l$), H($h_r$)) + 1
	- bF = (height of left subtree) - (heigh of right subtree)

			//Balance factor code
			if (bF < -1){
				rotateLeft();
			}
			if (bF > 1){
				rotateRight();
			}
# Rotations: 
Fixing imbalances in the tree so that searching is at ***worst***: $\Theta(log(n))$
When rotating, we are swapping two nodes and then moving the subtrees around so that they don't break the invariant of being a [[Binary Search Tree]]. So if a subtree has to be $>y$ and $<x$ that subtree will still have those properties after the rotation.

##### 1. Left rotations
- Performed when the ***right*** subtree of a node is ***heavier*** than the ***left*** subtree
- Image two Nodes x, y where x.right = y;
	- In the left rotation y becomes the root
	- And then y.left becomes x;
	- All other subtrees fall into the place they should be
##### 2. Right rotations
- Performed when the ***left*** subtree of a node is ***heavier*** than the ***right*** subtree
- Imagine two Nodes x, y where x.left = y; 
	- In a right rotation y becomes the root (goes to place where x is)
	- And then y.right becomes x;
![[Pasted image 20240514145332.png]]
When balance of a node is >1 or < -1 is the balance factor of the child (in the direction of the imbalance) has an **OPPOSITE** sign, then a ***double*** rotation must occur
##### 3. Left-Right rotations:
Do **left** rotation on child, then do a right rotation on root.
##### 4. Right-Left rotations
Do **right** rotation on child, then do a left rotation on root.
![[Pasted image 20240514150930.png]]
^ this is when a RIGHT-LEFT rotation is needed

