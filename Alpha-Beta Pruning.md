- (With the Minimax algorithm)

# How it works
"If the best we can do on the current branch is < the worst we can do elsewhere, there's no point continuing on this branch"
### $\alpha$ is the worst we can do
- Associated with **MAX** nodes
- never **decreases**
### $\beta$ is the best we can do
- Associated with **MIN** nodes
- never **increases**
## We **STOP** if $\beta < \alpha$
- Initially $\alpha = -\infty$ & $\beta = \infty$
##### Can think about it like this:
- If we're on a max node we're updating $\alpha$ and increasing it
- If we're on a min node we're updating $\beta$ and decreasing it
# Example
![[Pasted image 20241228162251.png]]
Here the black (and one red one) show which branches get pruned
- All the bottom ones are shown for clarity but they wouldn't be generated if pruned
The example follow a left-first traversal of the tree
In the first pruning where the 5-9 branch is pruned it looks wrong as 9 is clearly the max, but as the next line is min it doesn't matter what that branch is it wouldn't be picked (even if it was lower because we are on a max branch!)
- At first we check 2, is 2 < $\infty$ no so move on and we check 3, 3 > 2 so we INCREASE $\alpha$ as it never decreases and check if 3 < $\infty$ no so we move on
- This then moves back up to the min node and we assume 3 and pass to the min node that $\alpha = -\infty$ and $\beta = 3$
- Then we check 5, is 5 < 3 yes okay so we prune and we stop
- $\alpha = 3 \space \&  \space \beta = \infty$ is given to the max node at the top

