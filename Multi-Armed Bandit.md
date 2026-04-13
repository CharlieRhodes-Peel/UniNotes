It's a problem in decision-making where an agent must choose between multiple options (called *"arms"* ) to maximise total rewards over time. Similar to a gambler trying different slot machines with unknown payouts. It involves balancing exploration (trying new options) and exploitation (choosing the best-known option) to achieve the best outcomes.

# $\epsilon$-greedy algorithm
- `r = Random.RandFloat(0,1)`
- `epsilon = 0.05 #idk lecture says around here` 
```
if (r > epsilon):
	# Pull the best arm known
else:
	# Pick a random arm
```
Then repeat until the budget is exhausted

# $\epsilon$-first algorithm
- `inital = epsilon * budget`
```
while (moneySpent < initial):
	#Pull arms in sequence
while (isPossibleToPullMoreArmsWithinBudget):
	# Pull best affordable arm (average quality per cost)
```
- This divides exploration and exploitation into two distinct phases.
- First gather information about quality, then start to exploit

# Thompson Sampling
- Keep a prior for each arm
```
while (canPullMoreArms):
	for each arm in arms:
		# Sample from its prior
	# Pull the arm with the best sample
	# Update prior of arm
```
- Naturally **explores** arms that are promising
- Starts to **exploit** as uncertainty drops

# Performance evaluation
![[Pasted image 20260327131130.png]]
