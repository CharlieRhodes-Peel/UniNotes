# Summary
**Rank aggregation** is the process of combining **multiple** ranked lists into a **single** consensus ranking. For example: algorithms, voters, search engines, judges, etc may rank the **same thing** in different **orders**. You want a unified ranking that best **reflects** **all** their **inputs**.
## Learning outcomes
Just listing out the learning outcomes from these notes, make sure to cover these and then revise these with flashcards!
#### Apply a range of voting rules to rank aggregation
- Plurality/(majority) vote - *item ranked 1st most often wins*
- Borda count - *assign points based on position, and sum them up*
- Borda count with Black's rule - *picks the Condorcet winner if one exists, else does borda count*
- Copeland - *Each candidate is scored based on head-to-head victories minus loses*
#### Explain and apply the Condorcet criterion
#### Can use these metrics to evaluate the quality of an aggregated ranking
- Spearman's footrule - *sum of how much an element has moved compared to another ranking*
- Kendall-tau - *number of head-to-head disagreements*
#### Apply two above metrics to optimally aggregate rankings

# Voting Rules

## Plurality Voting - Most ranked 1st wins
Each candidate gets **one** point for every *preference order* that ranks them first. Therefore, plurality looks to rank candidates based on the number of times they are the preferred one.
- The winner is the one with largest number of points

###### NOTE! This method only finds **one** winner! (ikr like wth)
### Example
What is the aggregated ranking using plurality voting for the following?
![[Pasted image 20260514210319.png]]

		 Number of times ranked first:
		 A = 1
		 D = 2
		 B = 1
		 C = 1

And therefore the winner is **D**!

## Borda Count
Each voter assigns a score to each of the n options, where n is the number of ranked **items**. The scores range from n-1 (highest) to 0 (lowest)

### Example:
Lets take the same example from plurality voting again
![[Pasted image 20260514211047.png]]

		In this scenario the points are as follows:
		A = 3 + (2*4)            = 11
		B = 3 + 2 + (1*3)        = 8
		C = 3 + (1*2)            = 5
		D = 3*2                  = 6

So in this scenario our winner is **A**!

With the aggregated ranking going `A>B>D>C`

## Borda Count with Black's Rule - The sneaky one
This one's a little a little cheeky in my opinion. It actually **Satisfies** the **Condorcet criterion** by doing the following

**If a Condorcet Winner exists** - pick that one 
**Otherwise** - use Borda Count
## Copeland Method
This one also **Satisfies** the **Condorcet criterion**
- Each candidate is scored based on it's head-to-head battle victories, minus it's loses
- Also works when there is no Condorcet winner!

### Example:
If we have a look at the following
![[Pasted image 20260514214502.png]]
```
A wins 2 loses 1
B wins 1 loses 2
C wins 0 loses 3
D wins 3 loses 0

Therefore D is the winner!
```
And we also get an aggregated ranking of `D>A>B>C`

# The Condorcet's Paradox
Tells us that in scenarios in which **no matter** which **outcome** we choose, a **majority** of voters will be **unhappy**.
### Hypothesis
Consider the following:
![[Pasted image 20260514211639.png]]
With plurality voting **AND** borda count we have *no winner*. And *whatever* option is chosen $2/3$ of people will be upset! (which is a *majority*)

## The Condorcet Criterion
A voting system is said to satisfy the **Condorcet Criterion**, if it always chooses a **Condorcet winner** *when* one *exists* 

A **Condorcet winner** is the candidate who *always* wins if the two candidates were to be in a **head-to-head**. But these winners **do not always exist** (the paradox!) 

### Example
Does a Condorcet winner exist within these rankings?
![[Pasted image 20260514212600.png]]
A vs B = A wins
A vs C = A wins
A vs D = D wins
D vs B = B wins

Therefore, without doing anymore head-to-heads we can see that a Condorcet winner **doesn't exist** because in all match-ups at some point A,B,C and D lose.

# Distance Metrics
Used the evaluate the quality of an aggregated ranking, used to compare different aggregate ranking methods

These metrics assume that there is a "*true ranking*", as if there is a "correct answer"
## Spearman's Footrule 
Is the sum of the displacements, i.e the total distances all elements are moved from another ranking

###### Note: Spearman's Footrule can be solved in polynomial time using the Hungarian algorithm
### Maths
#### $S(p,q) = \sum^{}_{i \in X} |p(i) - q(i)|$
Where:
- X is a finite set of candidates
- p and q are two rankings of candidates in X
- and as such p(i) and q(i) are the position of candidate i in the rankings in p and q respectively

### Example
If we have a look at the different rankings below:
![[Pasted image 20260514222236.png]]
```
We see that:
dist. betw. A = 1
dist. betw. B = 2
dist. betw. C = 2
dist. betw. D = 1

Therefore total sum is 6 
```
The distance between p & q is $\therefore$ 6

## Kendall-Tau 
We count the number of head-to-head disagreements between two rankings

###### Note: Minimising the Kendall-tau distance is NP-hard
### Example:
Again consider the below example again:
![[Pasted image 20260514222236.png]]
```
So lets tally up all those pairwise (head-to-head) disagreements
A vs B = agree     = 0
A vs C = DISAGREE  = 1
A vs D = agree     = 0
B vs C = DISAGREE  = 1
B vs D = DISAGREE  = 1
C vs D = agree     = 0

Therefore the total sum is 3!
```
Kendall-Tau method says the distance between p &q is 3

# Using Distance Metrics to pick a good ranking
Basically, pick your distance metric of choice, then calculate the distances of rankings against all possible rankings, pick the one with the least distances.

### The maths
#### $r^{*} \in \arg \min_{r \in R} \sum^{n}_{i=1} D(r,r_i)$
Where:
- X is the set of candidates
- n is the number of voters
- r_1, ... r_n are the rankings given by the voters
- R is the set of all possible rankings over X

### Example
So at the top we have 5 different votes for 3 candidates. We check each of these against **every possible ranking** of the 3 candidates. In this example we are using **Spearman's footrule**
![[Pasted image 20260514223557.png]]
And as you can see A>B>C is the optimal aggregated ranking :)

If we were to do the same with **Kendall-tau** 
![[Pasted image 20260514223849.png]]
We see that B>A>C wins !!