---
aliases:
  - PD
  - Default Probability
---
# Definition 
The ==conditional== probability of default within a one year horizon is called Probability of Default (or just PD), conditioning on the company does not default before this year.

Actually the survival probability, we can treat each-year default as an independent event, and use the probability formula to get the probability of default in a particular year.
	Probability of surviving one year: $1-\text{PD}$
	Cumulative Probability of default in two years: $1-(1-\text{PD})^2$ 
	Cumulative Probability of default in $T$ years: $1-(1-PD)^T$
	Or, if the $PD$ is not constant, $1-\prod_{i=1}^T(1-PD_i)$ 

# Cumulative Probability of Default
An **unconditional** probability, measure the total probability of default before $i^{th}$ year