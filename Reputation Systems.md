### What do we trust as humans?
- It's subjective - Personal experience
- Reviews
- Word-of-mouth
- ...
### Reputation vs [[Recommender Systems]]
##### Similarities
- Both use ratings provided by users
- Both provide a ranking based on these ratings
##### Differences
- Reputation is based on the assumption of a shared consensus - ideally is an *objective* measure
	- Whereas [[Recommender Systems]] relies on people having *differences* with preferences, but assumes *some* users have similar interests 
- Designed to address asymmetric information. Such as with the [[Lemon Problem]]
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


