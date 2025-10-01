---
tags:
  - MFM714
aliases:
  - EAD
Page: "11"
---

> [!Description]
> It is the percentage of the initially undrawn amount that gets utilized when default happens. 

The value is dependent on covenants and credit ratings.
Counter-intuitively, good companies have higher EAD. Reasons:
- They utilize less proportion of the committed when performing
- They probably have higher committed amounts ($N$, the notional value)
- They may have lax covenants and many lawyers to make sure they can draw down during distress.
Also counter-intuitively, EAD can be higher than 100%, when the debt-holder does not want the other party to go bankruptcy and ends up in lending more, or less than 0%, when some already amount gets paid back earlier.

# Modeling EAD
## For Committed Line
The book value of a loan when default does not happen: $s_i=P_i$ where $P_i$ is the amount of principle drawn before the default.
The book value of a loan when default happen: $$\begin{aligned}s_i &= P_i(1-LGD)+(N-P_i)EAD(1-LGD)-(N-Pi)\cdot EAD\\&=P_i(1-LGD)-(N-Pi)\cdot EAD\cdot LGD\end{aligned}$$
## For Uncommitted Line
$EAD=0$ as the bank will immediately stop lending once you default.

## Problem
1. How to determine $N$? Percentage of the undrawn amount as of what date prior to default? Have seen that using draw and committed amounts as of 2 years prior to default tends to be the most effective