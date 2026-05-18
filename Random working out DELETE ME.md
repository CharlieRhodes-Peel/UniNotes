if we have a latin squares lets say it goes



|     | C1           | C2           |
| --- | ------------ | ------------ |
| F1  | P1 \| C1F1P1 | P2 \| C2F1P2 |
| F2  | P2 \| C1F2P2 | P1 \| C2F2P1 |
ig you could also theoretically have


|     | C2             | C1             |
| --- | -------------- | -------------- |
| F2  | P2 \| P2,C2,F2 | P1 \| P1,C1,F2 |
| F1  | P1 \| P1,C2,F1 | P2 \| P2,C1,F1 |


tp = 2
fp = 3
tn = 43
fn = 2

accurary = tp + tn / 

2 + 43 


utlity:

40 * 0.2 = 8 
30 * 0.4 = 12 
20 * 0.6 = 12
10 * 0.8 = 8

30 * 0.2 = 6
20 * 0.4 = 8
10 * 0.6 = 6


5 candidates so first place is 4


A = 4 * 2 + 3 * 2 + 2 = 16
B = 0 + 1 + 4 + 4 + 3 = 12
C = 3 + 2 + 0 + 0 + 1 = 6
D = 1 + 3 + 1 + 2 + 0 = 7
E = 2 + 0 + 2 + 1 + 3 = 8




| Pos | Neg | Neu |
| --- | --- | --- |
| 4   | 1   | 0   |
| 1   | 4   | 0   |
| 0   | 2   | 3   |
| 3   | 2   | 0   |
| 0   | 4   | 1   |

Then you calculate the weights for each user
Alice = 4 + 4 + 3 + 3 + 4 = 18
Bob = 4 + 4 + 2 + 2 + 4 = 16
Carol = 4 + 1 + 3 + 3 + 1 = 12
Dave = 1 + 4 + 3 + 2 + 4 = 14
Eve = 4 + 4 + 3 + 3 + 4 = 18

Then we work out their weights by doing their weight * No. Users / total weight sum

So with that we would have (doing these to two demical places)

Alice = 18 * 5 / 78 = 1.15
Bob = 16 * 5/78 = 1.03
Carol = 12 * 5/78 = 0.77
Dave = 14 * 5/78 = 0.83
Eve = 18 * 5 / 78 = 1.15

Then we can remake the table from above with the new weights


| Pos  | Neg  | Neu  |
| ---- | ---- | ---- |
| 4.1  | 0.83 | 0    |
| 0.77 | 4.16 | 0    |
| 0    | 2.18 | 2.75 |
| 3.07 | 1.86 | 0    |
| 0    | 4.16 | 0.77 |

So you can see that the the weights are now applied to the results! In the case of review 3 it actually ambiguates the data more. This is why this calculation should be run again until the weights converge

Probability practise #1094570349751

What are we trying to find?

let P(1="n/a", 2="w") = P(obs)

P(r | obs) = P(obs | r) * P(r) / P(obs)

P(1 = "n/a" | r) = 0.3
P(2 = "w" | r) = 0.3 

P(obs | r) = 0.3 * 0.3 = 0.09

Need to find P(obs)

P(obs,r) = P(obs | r) * P(r) = 0.054
P(obs,w) = P(obs | w) * P(w) = ?

Need to find P(obs | w)

P(obs | w) = 0.1 * 0.5 = 0.05

Therefore P(obs,w) = 0.05 * 0.4 = 0.02

Hence P(obs) = 0.054 + 0.02 = 0.074

Then we can find out the final answer

P(r | obs) = 0.054 * 0.6 / 0.074 = 0.4378378378378378


