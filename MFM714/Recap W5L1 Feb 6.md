---
tags:
  - Recap
  - MFM714
---
The choice of the capital models also depends on:

1.  Who is the originator? 
2. The role the originator is playing?
	1. Full role: the originator consider a single loan as an organic component of the whole capital allocation process. 
	2. Partial role: the originator considers the correlation with other loans but on a monthly basis
	3. None: the originator only aims to get the best price. 


## Counterparty Credit Risk
Arised when the financial contract has a positive value to you, your counterparty may default and do not perform and this is the counterparty credit risk. The total amount that the counterparty could owe you is called the [[exposure]].

We can generate scenarios of the potential future counterparty credit risk through P space probability across times and scenarios. For each scenario, we do care about the number of the factors within The market risk model could have many factors like 12 or more since we are only consider a 10-day curve. But for credit risk, we might be interesting in a longer length of time horizon, and that many factors can break down our yield curves totally. Ideally we can have two or three different factors, and to determine which variables are included, [[PCA]] technique is used. 

Then we need to simulate the implied volatility, too. But to construct the volatility surface, where the term to maturity and stock prices are changing. Since we are doing so across the time horizon, it means we need to consider the volatility surfaces as constantly and daily change.