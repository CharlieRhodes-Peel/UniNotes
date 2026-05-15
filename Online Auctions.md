# Summary
Auctions give items a **dynamic** price based on competition. Online, items are essentially found via a **price** **discovery** mechanism. Therefore **decentralised** computation is done by the "crowd" (kinda like a [[Human Computation]] [[Recommender Systems]]). Examples of where these are found are: eBay, Display advertising, and the sponsored search on search engines

In all auctions there is the **private value** a bidder is willing to pay for that item, what they **think** they item is **worth**, and their **bid**, which may **depend** on what it is believed other *will* bid. Conceptually there is also a measure of a bidder's "*willingness to pay*"

The revenue equivalent theorem states that given it's 4 assumptions above bidders, each auction type *does* produce the **same** expected *revenue* to the **auctioneer**.
## Learning Outcomes
##### Understand where and why are online auctions used (look summary)
##### Know the 4 main types of (single-item) auctions
- English - *the standard auction type*
- Dutch - *where the price starts high, auctioneer decrements price, item goes to first to bid*
- Sealed-bid first price - *one round, bids placed in envelope and highest bid wins*
- Sealed-bid second price - *same as above, highest bid wins BUT pays second place price*
##### Understand Bidder's behaviour in auctions - Strategy
##### Understand potential problems with auctions
- Winner's Curse - *When the winner pays more than the item is worth*
- Bidder collusion - *Two or more bidder manipulate bids to keep price low*
- Corruption: Lying auctioneer - *auctioneer takes bribe and/or lies*
- Sniping - *placing bid at the last minute to avoid bidding war*
##### Sponsored search

## Terminology
- **Bidder** = someone partaking in the auction
- **Dominant Strategy** = the best thing to do irrespective of other's
- **Private Value** = How much a bidder is willing to pay for an item
- **Utility** = how much "profit" one has made between their private value and the take home price 
# Types of auctions
## English - The "Normal" type
This is most commonly known type of auction. Each bidder is free to raise the bid, and when bidder is willing to raise anymore, the auction ends. The highest bidder wins the item at the price of there bid

### Strategy - Dominant
The best strategy is to bid a **small** amount more than the **current** bid and stop when your **private value** is reached.

This strategy is *dominant*, it's the best thing to-do, irrespective of other's strategies. 
## Dutch - The upside down English
The auction **starts** at a high price. The *auctioneer* **lowers** the price until a *bidder* makes a bid **equal** to the current offer price. The good is then allocated to the bidder that made the offer; the agent pays the price they bid
## Sealed-bid first price
There's 1 round only! The bidder's all submit offers in a sealed envelope at once. The good is allocated to highest bid, the winner pays the price they bid!
#### Where is this used?
- Usually for procurement by companies and organisation
- Or for government project contracts
### Strategy - No Dominant
Bidder's will try to speculate about the bids of others, an estimate the probability of the highest bid.

The "**best**" strat is to *shade bid*: where you bid less than the true valuation, but how much less depends on what others bid.

The aim is to maximise the expected *utility*

#### Example
```
yourPrivateValue = 300

# There's a 40% chance that the highest bid (except you) is 150, 40% chance that 
# it will be 210, 20% chance it will be 240. So what's you're best strat?

utility = chanceOfBid * (yourPrivateValue - bid)

# So if you bid 151... utility = 0.4 * (300 - 151) = 59.60
# If you bid 211.......utility = 0.8 * (300 - 211) = 71.20
# If you bid 241.......utility = 1 * (300 - 241)   = 59

# So your best strat is to bid 211

```

## Sealed-bid second price (Vickrey) - A weird one
Goods are awards to the bidder that made the highest bid; **BUT** they pay the price of the **second** highest bid.

The method avoids wasteful effort spent on counter speculation, and it ensures that the bidder with the highest *private value* receives the item (so it's efficient) 
#### Example
```
# Suppose we have 3 bidders who bid the following
bidder[0] = 100
bidder[1] = 200
bidder[2] = 300

# bidder[2] wins and they pay 200!
```
### Strategy - Dominant
The dominant strategy is actually to just bid your private value upfront!

Lets assume the max bid is **above** our private value. If we underbid, we're still losing anyways. If we overbid, we might win but we end up overpaying.
If we then assume that the max bid is **BELOW** our private value. If we underbid, we *could* lose the item. And if we overbid, there is no change to the outcome

$\therefore$ the best strat is just to bet your private value upfront

# Strategy comparison
*English* and *Vickrey* are **strategically equivalent** because the *dominant strategy* is to bid up to the true private value. Therefore the winner in both fields is the bidder with the highest true private value

*Dutch* and *first price sealed bid auctions* are **strategically equivalent** because the bid only matters if it's the highest, no information is given away during the auction.

#### From the seller's perspective - what's most profitable?
All 4 auction types listed here produce the same expected revenue to the auctioneer provided that:
- The bidders are *rational*
- The bidders are *risk neutral*
- The assumption that each bidder **has** a private value holds
- Bidders are symmetric - *they all hold same beliefs about probability of bids made by others*
###### This is known as the Revenue Equivalence Theorem

# Problems with Online Auctions
In 2009, 25% of internet fraud complaints concerned online auctions! As such, a main problem with auctions is that they are prone to fraud, as well as other's that we will look at here.

An additional problems with auctions that isn't listed below that I wanted to mention was the risk of low profit from the seller. This can be fixed by reserving and starting at that price (or stopping in the case of dutch auctions)

## Winner's Curse
When the winner pays **more** than the item is **worth**. This generally happens when the **value** of the item is **unknown** / uncertain.
The winner realises that other participants estimated a *lower market value* for the item. It was just the winner who made the largest positive error in their valuation
##### How to prevent
- Take winner's curse into account when bidding
- **Open-bid auctions** provide more **information** about the valuation of other bidders, allowing bidders to **incorporate** this information in their decision-making
## Bidder Collusion
When 2 or more bidders form bidding rings to **manipulate** the auction. Buyers may collude to try and keep the final sale prices low. The key challenge however is in **identifying** and then **prove** that colluding occured
##### How to prevent
- Governments make it illegal
- Auction sites make it a condition of joining the auction that the bidders do not collude

## Auctioneer Corruption
Auctioneers may be bribed and thus lie about submitted bids. For instance, in a sealed-bid Vickrey Auction, the auctioneer has an incentive to lie about the amount bid by the second-highest bidder
##### How to prevent
- Can only be checked if all bids are *revealed* **after/during** the auction (but this does raise *collusion* threats)

## Sniping
When an auction closing time is fixed (eBay), can snipe it right at the end. This strategy prevents a bidding war, and being outbid by others.
##### How to prevent
- Flexible deadline
- Sealed-bid auction

# Sponsored Search
80% of google advertising revenue comes from advertising, hence it's pretty important. 

- Advertisers submit *bids* on **keywords** and the *maximum* amount they are willing to pay for a user *clicking* on their ad (**PPC**)
- Search Engines then uses this auction mechanism to allocate ads to available slots
## Payment Models
There are many different type of payment models to advertisers. 
### Pay-per-impression - Pay for how many times shown
An "*impression*" is when an ad is displayed. It's based on traditional advertising in printed media. It's still widely used in display advertising.
### Pay-per-click
Only pay when clicked, nowadays all search engines use this model

In terms of sponsored search, different keywords attract different interests. Some keywords are very expensive. And so the goal is to maximise price times probability of a click

##### $Profit = \sum^{}_{i \in positions} payment_i \times CTR_i$
Where:
CTR = Click-through-rate
### Pay-per-transaction
The cousin of pay-per-click. Except only pay when an actual purchase is made. You need to therefore track this, and it can be hard to attribute where the person came from when a purchase is compete.

## Allocation
Allocation looks at answering the question, how to design an auction that maximises the search engines profits? 
### Simple Approach - Highest bid first
- Does what it says on the tin
- Not the best though, could lead to low-quality but high bid products

### Google's Quality Score
Is calculate on a number of factors listed below, however the exact formula is a secret
- Historic CTR
- Relevance of the ad to a search
- Quality of the landing page

So to make a simplification of things we could says that: $b_i \times q_i$ determines allocation
Where:
- $b_i$ is the bid, and $q_i$ is the quality score

## Payment - Auction Types
### First-price auctions
- Leads to inefficient results
- Prices fluctuate a lot due to speculation
### Generalised second-price auctions
- Based on Vickrey auction principle
- Pay the smallest amount you could have bid and still retain the same position (see below for how that's calculated)
- The payment is *never* more than the bid (and is typically less)
- The auction is not truthful however.
	- Bidders might prefer lower spots to increase utility
- GSP auctions do not fully capture preferences: bid is for one slot and not each slot
#### How it's calculated !! VERY IMPORTANT TO EXAM PROBABLY
##### $p_{x_r} = \frac{b_{x_r+1} * q_{x_r+1}}{q_{x_r}}$
Sorry this is kinda hard to read
Where:
$x_r$ is the bidder ranked in position r
$p_{x_r}$ denotes the payment of bidder in position r
$b_{x_r}$ the bid of a the bidders ranked at position r
##### Example
Suppose we have 2 slots available and the following bidders

|              | Quality Score | Bid |
| ------------ | ------------- | --- |
| Advertiser 1 | 0.6           | 10  |
| Advertiser 2 | 0.9           | 7   |
| Advertiser 3 | 0.4           | 5   |
```
# Calculating allocation
A1 = 6
A2 = 6.3
A3 = 2

# So A2 gets slot 1 and A1 gets slot 2
```

But how much do they have to pay?

```
[Slot 1]: p_A2 = (b_A1 * q_A1) / (q_A2) = (10 * 0.6) / 0.9 = 6.67
[Slot 2]: p_A1 = (b_A3 * q_A3) / (q_A1) = (5 * 0.4) / 0.6 = 3.33  
```

