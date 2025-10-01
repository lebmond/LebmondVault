## Contemporaneous Defaults
We first map the cumulative [[probability of default]] overtime of two individual obligors to normal distributions, respectively. We draw two independent observations from their distributions, respectively, and derive their correlated returns given their asset correlation.

Though their correlation of contemporaneous default weakens as the time horizons gets larger, it is worthy to point out that for the first bucket (i.e.  they all default during the first year), the cumulative probability of default is the same between the reduced form model and structural model.

## Correlation Issues
The calculated probabilities of joint default is not the same under two different methods:
1. Normal [[Copula]]
	   Normal copula method is like doing a single draw for the whole time horizon. This is done by construction a transition matrix that spans the entire time horizon using their transition matrix (singular, since we assume these two companies share the same transition matrices)
2. Consecutive Yearly Drawn
	   Consecutive Yearly draw takes more steps and draw one observations for each step.
And using the consecutive yearly drawn could lead to change in asset correlations, (and it is ==non-linear==). We need to change the time steps to maintain the consistency in the joint probability of default.

Stepping: We use the repeated Markov chain to characterize the joint probability of default in any given year.
One draw: reduced normal copula form, you take two random normal draws from A and B probability of default models, and then you know when they would go default.
Zero Correlation: serve as the benchmark to see how two zero correlation corporation's JPD evolves.

The problem with correlation is that the normal copula, calculating the JPD through one and only one steps ==**overestimate the JPD**== while the consecutive yearly draws causes the JPD to decrease or converge too quickly. The most ideal status is somewhere between these two extremes, preferably one smooth shift from the stepping curve to the consecutive yearly drawn curve.
