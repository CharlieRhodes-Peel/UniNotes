# Summary
This is a technique used in Modern [[Recommender Systems]] which infers 'latent' factors from rating patterns. It's a computational alternative to human-assigned factors. Instead of manually labelling movies as "action" or "romantic", you let the maths _discover_ hidden patterns in ratings automatically. These hidden patterns are called **latent factors**.

• Characterises items and users by vectors of latent factors inferred
from item rating patterns.
• Good scalability and predictive accuracy
• Can be used to incorporate both explicit and implicit feedback
• Effective for binary interaction data
• SGD is easier to implement and faster than ALS
• Parallel implementation can be used for ALS to solve for $q_i$'s and $p_u$'s independently


# The Steps
1. **Start with a big sparse ratings matrix** (orange matrix on diagram) where the rows are the users and the columns are items, where most cells are empty because users haven't rated most things
2. **Split this into two smaller matrices**
	- You get a **user matrix** `p` - each user gets a vector describing how much they connect to each latent factor
	- And an **item matrix** `q` - each item gets a similar vector
3. **To predict a rating** you just take the *dot product* of a user's vector and an item's vector (see maths section)
4. **Training** means adjusting those vectors until your predictions match the real ratings as closely as possible, there are two ways to do this **ALS** and **SGD** both of which are explained below
	- **ALS (Alternating Least Squares)**: Fix one matrix, solve exactly for the other, then swap. Repeat. Works well for [[Parallelism]] tasks
	- **SGD (Stochastic Gradient Descent)**: Pick a random rating, see how wrong your prediction is, and nudge both vectors slightly in the right direction. Easier to implement than ALS and is generally faster
5. **Regularisation** (the $\lambda$ term) is added to prevent over-fitting - essentially a penalty for vectors that grow too large

## Diagram
![[Pasted image 20260323160031.png]]

# Maths
The item vector in latent factor space is given by
### $q_i \in \mathbb{R}^{f}$

where: 
- vector $q_i$ = the extent to which item $i$ connect to each factor
- $f$ = dimensionality of latent factor space
- $\mathbb{R}^f$ = latent factor space

The user vector in latent factor space is

### $p_u \in \mathbb{R}^f$

where:
- vector $p_u$ = extent to which user u connects to each factor

Matrix $q[N_{items}, N_{factors}]$ and $p[N_{users}, N{factors}]$

Remember, The factor dimension != Item / User attribute (e.g user age, film genre)

## Rating Prediction
The rating prediction is calculated by doing the dot product ($r^{'}_{ui}$)

### $r^{'}_{ui} = q_i \times p_u = score$
### $r^{'}_{ui} = \sum^{f}_{k=1}q_{ik}p_{uk}$
### $r^{'}_{ui} = q_i^{T}p_u$
### Diagram
![[Pasted image 20260323161006.png]]


## Implementation
The idea is to minimise the error between the predicted rating ($r^{'}_{ui}$) and the actual rating ($r_{ui}$) across the training set

- Training set of (u,i) rating pairs
### $K = \{ (u,i): where \space r_{ui} \space is \space known \}$

Objective function
### $min_{q^*,p^*} \sum^{}_{(u,i) \in K} (r_{ui} - q^T_u p_u)^2$




# Dealing with sparsity
Training on relatively known few entries can lead to over-fitting. And [[Imputation]] can be expensive and can also distort the data considerably. So you should use this technique on only regularised models to avoid over fitting

# ALS vs SGD
This section goes over the differences between ALS and SGD briefly described in the steps section.
## ALS
Alternates between fixing the $q_i$'s or $p_u$'s and recomputing the others by solving least-squares problem.


Regularized Square Error to learn factor vectors $q_i$ and $p_u$

### $min_{q^*,p^*} \sum^{}_{(u,i) \in K} (r_{ui} - q^T_u p_u)^2 + \lambda(\sum^{}_{i}||q_i||^2 + \sum^{}_{u}||p_u||^2)$

where: 
‖ $q_i$ ‖ = magnitude of vector = sqrt(sqr($q_1$) + sqr($q_2$) ... sqr($q_k$))
$\lambda$ value controls the extent of regularisation to avoid overfitting

## SGD - Stochastic Gradient Descent
For each randomly chosen training pair (u,i) predict $r^{'}_{ui}$ compute error and modify user and item vectors
### Pseudocode (for training)
```
# Training input: ratings(N_user, N_item) with empty values removed

N_factor = 40 # (Usually between 20 and 100)
learning_rate = 0.1 # Gamma value
regularisation = 0.01 # This is the lambda value

# Then randomly init item vector q(N_item, N_factor)
# Then randomly init user vector p(N_user, N_factor)

for k in range N_iterations:
	# Make a randomly suffled set of (u,i) pairs
	
	for l in range UI_pairs:
		predicted_rating = q[i] * p[u]
		actual_rating = ratings(u,i)
		error = actual_rating - predicted_rating
		p(u,*) += learning_rate * (error * q(i,*) - regularisation *                       (p(u,*))) 
		q(i,*) += learning_rate * (error * p(u,*) - regularisation *                       (q(i,*))) 
```
### Maths
Prediction error:
### $e_ui = {1}\div{2} \times (r_{ui} - q_i^Tp_u)^2 + regularizationTerm$

And then modify user and item vectors adjusted by $\gamma$ learning rate parameter
![[Pasted image 20260323170353.png]]

# Other Modifications
You can try setting up a grid search to optimise the parameters such as number of latent factors, learning rate and regularisation term.

Could also include bias terms, modelling observed variations in rating values associated with biases from users or items