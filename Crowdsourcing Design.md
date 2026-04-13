How do we try different crowdsourcing designs? If we are designing [[Recommender Systems]], how do we compare which one works best in practise? We use **Experimental Design** to scientifically test an **tune** a system to find an optimal design.

# The Experimental Approach
This sections uses a website as an example. How do we optimise the landing page to convert most users to interacting with the site more?

First we answer the question, what do we measure success with? Well there are lots of things like:
##### Web Analytic - Data -> USE GOOGLE ANALYTICS FOR THIS GENERALLY <-
- IP addresses / geopgraphical location
- How many unique visitors are there
- Browser / plugins used
- Keywords that led to the page
- Which pages were viewed and for how long
- Referring sites
- Conversion rates (ROI)

##### Approach
Once we have decided the appropriate measures we can experiment with different page and site layouts in order to improve these metrics! There are even sites for this very purpose like **Google Website Optimizer**

# A-B Split Testing
Randomly assign one of two webpages to new visitors - A is the "original" and B is the "challenger" and then you see what performs better!

| Advantages                                     | Disadvantages                                                                                                 |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Easy to test, implement and analyse            | Cannot test all possible combinations or capture interdependence between other variables                      |
| Flexibility in defining variable/factor values | Not possible to discover which elements contributed the most, Because too many things change at the same time |
|                                                | Inefficient form of data collection (for website design)                                                      |
# Multivariate Testing
This is where you simultaneously gather information about multiple factors / variables, changing **one-factor-at-a-time** (*OFAT*). 
- Full factorial design - looks at all combinations of variables
- Fractional factorial design - only looks at a subset

## One-factor-at-a-time (OFAT)
Suppose you have 3 factors: page layout `pl`, colour schemes `cs` and page content `pc`. You have 3 values for each... e.g `pl[0], pl[1], pl[2]`

You need to choose a base "*recipe*" lets say `(pl[0], cs[0], pc[0])`
- Now we need to test $1+2*3 = 7$ different recipes
	- `(pl[0], cs[0], pc[0])`
	- `(pl[1], cs[0], pc[0])`
	- ... and so on
There are a limited number of recipes, unbalanced (values have different number of occurences). Suppose we need 100 trails per recipe to obtain statistical significance

**The main point** of this design pattern is that we are testing **one factor at a time** against the base recipe

Can only be used to measure *main effects*

## Full factorial design
Considers all possible combinations. Suppose you have the same 3 factors from before

- This time we have a **total** list of possible **recipes** of $3^3 = 27$

We can test all combinations (balanced)

- But how many trails do we need? There are many recipes, so we want to minimise the number of trails

## Latin Squares
Latin squares have the same benefit that Full factorial design testing but with fewer recipes! How?

Each variable is evenly tested so it's balanced but it also reduces the number of recipes
### Diagram
![[Pasted image 20260405190240.png]]

