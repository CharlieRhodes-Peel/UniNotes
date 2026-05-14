Reputation system aim to help *asymmetric information* between sellers and buyers on the web. Avoiding potential **moral hazards** and *market failure*. 

### What do we trust as humans?
- It's subjective - Personal experience
- Reviews
- Word-of-mouth
- ...
#### Why the web poses challenges to this
- **Anonymity**: It's easy to fake an identity
- **No physical presence**: Doesn't allow for the traditional (perception of) trustworthiness through human interaction
- **Low cost of setting up a good looking web presence**: compared to bricks and mortar
- $\therefore$ the *asymmetry* of information is greater than in person
### Moral Hazards
Once a transaction has taken place, there is no incentive for parties to stick to the bargain. Like complete the payment, provide a follow-up. **BASICALLY, THINK KICKSTARTER AND OR PIRATE SOFTWARE**

A moral hazard is a situation in which one party gets invlovled in a risky event knowoing that it is protected against the risk and the other party will incur the cost
- An example:
	- If you are insured, there is less incentive to be careful. Similarly, if buyer has paid, there is less incentive for the seller to fulfil its part of the bargain.

#### How this differs from **adverse selection**
Adverse selection is due to asymmetry **before** the transaction, Whereas a **moral hazard** is about what happens *after* the transaction 

### Reputation vs [[Recommender Systems]]
##### Similarities
- Both use ratings provided by users
- Both provide a ranking based on these ratings
##### Differences
- Reputation is based on the assumption of a shared consensus - ideally is an *objective* measure
	- Whereas [[Recommender Systems]] relies on people having *differences* with preferences, but assumes *some* users have similar interests 
-  Reputation systems are designed to address asymmetric information. Such as with the [[Lemon Problem]]
	- Whereas [[Recommender Systems]] are *personalised*


### Calculating a Reputation Value:
##### Number of different ways:
- Simplest = average ratings
- Correct for user bias, i.e average w.r.t population average
- Weighted ratings with user's bias
##### But what about the confidence of this reputation?
- Simplest = No. ratings
- Statistical tests, e.g. standard deviation / variance of the distribution, p-values (when using probabilistic approach)

### Different Types of Reputation Evaluation: 
- Reputation values are often used to generate *rankings* 
	- Pagerank (google) is an example of this
	- TripAdvisor and similar websites rank hotels, restaurants, etc.

### Existing Reputations system examples:
- Ebay - Contains both a buyer and seller Reputation system 
- Amazon - Buyer reputation / Reviews on products
- Facebook - Like and other emotions and stuff i suppose


