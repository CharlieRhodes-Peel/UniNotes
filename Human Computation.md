Outsourcing computation to a crowd of people

For more about crowd sourcing look at [[Incentives]] and [[Expert Crowdsourcing]]

#### Learning outcomes
1. Publish HComp tasks on Amazon [[Mechanical Turk]]
2. Evalute whether a given problem can benefit from HComp
3. Design basic task workflows
4. Select and apply appropriate techniques for quality control:
	1. Majority voting
	2. Weighted Voting
	3. Expectation Maximisation
# What problems are suitable for HComp?
Problems that are **hard for computers** but **easy** for *humans*, and Ideally tasks that are quickly explained to non-experts,  fast to complete and ones that can be **decomposed** into **smaller** tasks. Results from tasks should be amendable to automatic **quality control** and *aggregation* (combining) .Also the tasks should be **robust** to some **noise**. To sum this all up **data collection**

# Amazon ![[Mechanical Turk]]
# Soylent : *Find-Fix-Verify* Pattern
Is a word processor with "a crowd inside". Text editing is a complex, open-ended task, and many people can get it wrong. Simply, they follow a **Find-Fix-Verify** Pattern:
- **FIND**: users highlight sections of a problem that need attention (e.g parts of a text that can be shortened, sentences that contain mistakes, etc.)
- **FIX**: Users propose improvements for the most commonly highlighted sections only (one improvement per user)
- **VERIFY**: Users vote on the best (or worst) improvements

You can see that this **DECOMPOSES** the problem down into simple **HCOMP Suitable** tasks! Each of these tasks could be posted to Mechanical Turk.

## Why it works so well
- Separates the **find** and **fix** users to avoid lazy users (those who focus on the easiest fixes)
- Local work enables parallel processing and allows edits to be mapped clearly to sections of text
- Verification ensure quality (workers often better at verification than producing high-quality output themselves)
- Decisions within each stage are independent
- Small tasks decrease the likelihood of errors

# Implementing HComp Workflows
Building and testing complex HComp workflows is challenging, they can be costly and take many hours or days to be completed. How do you debug / work on a system like this?

## The *Crash-and-Rerun* Pattern
Program is re-executed on failure, but some function results are cached:
- HComp results (HITs)
- Nondeterministic functions
- Functions with side effects
### Benefits of this
- Incremental development
- Easy to use
- Easy to add debugging output
### Diagram
![[Pasted image 20260310144533.png]]

# Quality Control
Can calculate some metrics to try and get some more accurate results from the data

| Metrics   | Equation                        |
| --------- | ------------------------------- |
| Precision | tp / (tp + fp)                  |
| Recall    | tp / (tp + fn)                  |
| Accuracy  | (tp + tn) / (tp + tn + fp + tn) |
where: 
```
tp = true_positive # Item recommended and item is relevant
fp = false_positive # Item recommended but item not relevant
tn = true_negative # Item not recommended and is not relevant
fn = false_negative # Item not recommended but is relevant
```

## Majority Voting - Most votes wins
The simplest aggregation method — whichever label gets the most votes wins.
- Assumes all workers are **equally reliable**
- Works better with **more voters** and **higher individual accuracy**
- Best to use an **odd number** of voters — with an even number, going from N-1 to N voters gives no benefit (ties are broken by a coin flip anyway)

### How many workers do you need?
With each worker having **p = 0.6** accuracy:
- 3 workers → P(correct) = 0.6³ + 3 × 0.6² × 0.4 = **0.648**
- 67 workers → P(correct) ≈ **0.95**

Higher individual accuracy means you need fewer workers:
- p = 0.7 → need ~15 workers for 0.95
- p = 0.8 → need ~7 workers for 0.95

## Weighted Voting
Used in **Galaxy Zoo** — classifying ~1,000,000 galaxies with ~150,000 participants.

The idea: **workers who agree more with others get higher weight**. This rewards reliable workers without needing ground truth labels.

### Steps
1. **Count votes** for each item/label combination
2. **Compute raw weight** per user — sum up how many others voted the same way they did across all items
3. **Normalise weights** — redistribute N votes (one per user) proportionally to raw weights (For each weight, do ((Num. Users ) / (Sum of each user's weights)) * weight
4. **Recompute** the vote table using weighted votes
5. *(Optional)* Repeat until weights **converge**

### Why it works
- Handles **ambiguous cases** better than majority voting
- Tends toward majority vote in clear cases
- Comparable to **expert classifications** in practice

### Additional quality measures used by Galaxy Zoo
- Removal of low-quality data
- Weights only calculated when a clear majority exists
- See *Lintott et al. (2008)* for full details

## Weighted Voting with Prior Knowledge
Rather than just counting agreements, we can use **confusion matrices** to model each worker's reliability more precisely.

A **confusion matrix** tracks how often a worker says X given the ground truth is Y:

|  | Says Kitten | Says Not Kitten |
|---|---|---|
| **Is Kitten** | P(says kitten \| kitten) | P(says not kitten \| kitten) |
| **Is Not Kitten** | P(says kitten \| not kitten) | P(says not kitten \| not kitten) |

Combined with a **prior probability** (e.g. P(kitten) = 0.5) and **Bayes' Theorem**, you can compute the true probability of each label given all workers' votes — weighting better workers more heavily automatically.

### General Form
$$P(GT | votes) \propto P(GT) \prod_{i} P(vote_i | GT)$$

### Where does prior knowledge come from?
- Previous interactions with the worker
- A reputation system
- **Gold standards** — tasks where the true answer is already known

### Pros and Cons
- **Pro**: Principled, more accurate, gives a probabilistic answer
- **Con**: Requires prior knowledge, does not learn from data

## Expectation Maximisation (EM)
Solves the chicken-and-egg problem: *what if we don't know worker quality upfront?* EM learns confusion matrices and classifies data **at the same time**.

Proposed by **Dawid and Skene (1979)**.

### Inputs and Outputs
- **Input**: Raw worker labels
- **Output**: A confusion matrix per worker + a probability distribution for each item's true label

### Algorithm
1. **Initialise** confusion matrices with reasonable priors (e.g. assume everyone is equally accurate)
2. **Step 1 (E-step)**: Estimate the true label for each item using current confusion matrices
3. **Step 2 (M-step)**: Update confusion matrices based on the newly estimated labels
4. **Repeat** until the matrices stop changing (convergence)

### Key Insight
Workers who consistently agree with the **estimated ground truth** get higher weight. Workers who seem to be random or contrarian get lower weight — all without needing any gold standard data.

### EM with Gold Standard Data
If some items have **known true labels**, these can be fed in to give EM a better starting point, potentially improving accuracy — though obtaining gold standard data is costly.

### Pros and Cons
- **Pro**: Flexible, learns from data, gives quality estimates per worker and probabilistic answers
- **Con**: Less intuitive, needs reasonable initialisation, more complex

---

## Summary: Quality Control Methods

| Method | Pros | Cons |
|---|---|---|
| **Majority Voting** | Very easy, intuitive | Needs many workers |
| **Weighted Voting** | Easy, reasonably intuitive | Tends toward majority opinion |
| **Weighted Voting (with Prior Knowledge)** | Principled, more accurate, probabilistic | Requires prior knowledge, doesn't learn |
| **Expectation Maximisation** | Flexible, learns from data, probabilistic, gives worker quality estimates | Less intuitive, needs good initialisation, more complex |
| **EM with Gold Standard** | As above but potentially more accurate | Gold standard data is costly to obtain |
