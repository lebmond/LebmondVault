For FRM Part II (https://www.google.com/search?q=FRM+Part+II), Market Risk Measurement and Management accounts for 20% of the exam weight (approximately 16 out of 80 questions). The curriculum transitions from basic definition concepts to deeply technical, quantitative models, and complex regulatory frameworks.
The core syllabus can be broken down into five distinct execution pillars, followed by a simulated exam-style mathematical scenario.

1. Advanced VaR and Expected Shortfall (ES)

Part II focuses heavily on the structural limitations of VaR and the implementation of coherent risk measures.
• [[Coherence of Risk Metrics|Coherence]] Requirements: 
• Extreme Value Theory (EVT): Used to model the actual shape of the distribution tails rather than assuming normality.
	• Block Maxima Approach: Uses the Generalized Extreme Value (GEV) distribution to model the maximum losses over fixed time blocks.
	• Peaks-Over-Threshold (POT) Approach: Uses the Generalized Pareto Distribution (GPD) to model all exceedances above a sufficiently high, predefined threshold.
• Parametric Extensions: Transitioning from static volatility to time-varying volatility using GARCH(1,1) models and implied volatility smiles/skews.

2. Fixed Income and Interest Rate Risk

This domain covers the modeling and hedging of complex yield curves and interest rate options.
• Term Structure Models:
	• Equilibrium Models: Vasicek (mean-reverting, but rates can go negative) and Cox-Ingersoll-Ross (CIR) (mean-reverting, rates stay positive).
	• No-Arbitrage Models: Ho-Lee and Black-Derman-Toy (BDT) (calibrated to perfectly match the current market yield curve).
• Mortgage-Backed Securities (MBS): Focuses on prepayment risk, Prepayment Speed Models (CPR/PSA), and isolating Option-Adjusted Spread (OAS).
• Volatility Smiles: Analyzing why deep out-of-the-money options trade at higher implied volatilities than at-the-money options (equity frown vs. currency smile).

3. Backtesting and Risk Model Validation

Models must be dynamically audited to ensure they do not underreport risk.
• Basel Traffic Light System: Regulators categorize VaR models over a 250-day testing window based on the number of exceptions (days where actual loss exceeded VaR):
	• Green Zone: 0 to 4 exceptions (No capital penalty).
	• Yellow Zone: 5 to 9 exceptions (Scales up the capital multiplier factor, \(\textstyle \mathbfit{k}\)).
	• Red Zone: 10+ exceptions (Presumed model failure; requires immediate model overhaul).
• Statistical Tests: Utilizing the Kupiec Unconditional Coverage Test (chi-square distributed) to verify if the probability of an exception matches the theoretical target (e.g., exactly 1% for a 99% VaR).

4. Regulatory Frameworks: The Fundamental Review of the Trading Book (FRTB)

FRTB introduces massive structural overhauls to bank capital calculations for market risk.
• The Shift to ES: Replaces 99% 1-day VaR with a 97.5% Expected Shortfall metric to capture tail risk.
• Liquidity Horizons: Moves away from a static 10-day holding period to varying liquidity horizons (ranging from 10 to 120 days) depending on the liquidity of the underlying asset class.
• Standardized Approach (SA) vs. Internal Models Approach (IMA): Tightens restrictions on using internal models and introduces strict desk-by-desk approval rules.

5. Quantitative Scenario: Cornish-Fisher VaR Calculation

When returns are non-normal (exhibiting skewness and kurtosis), standard parametric VaR will fail. The Cornish-Fisher expansion adjusts the standard normal critical value (\(Z_{c}\)) into a modified critical value (\(Z_{CF}\)) to account for these higher-moment asymmetries.

The Formula:

\(Z_{CF}=Z_{c}+\frac{1}{6}(Z_{c}^{2}-1)S+\frac{1}{24}(Z_{c}^{3}-3Z_{c})K-\frac{1}{36}(2Z_{c}^{3}-5Z_{c})S^{2}\)
Where:
• \(Z_{c}\) = Standard normal distribution critical value
• S = Skewness of the portfolio
• K = Excess Kurtosis of the portfolio
Let's calculate a 95% 1-Day Cornish-Fisher VaR for a $10,000,000 portfolio with the following parameters:
• Daily expected return (μ): 0.00%
• Daily volatility (σ): 1.50%
• Skewness (S): -0.60 (negative tail)
• Excess Kurtosis (K): 2.10 (fat tails)
For a 95% confidence level, the standard normal critical value is \(Z_c = 1.645\). Let's solve for \(Z_{CF}\):
\(Z_{CF}=1.645+\frac{1}{6}(1.645^{2}-1)(-0.60)+\frac{1}{24}(1.645^{3}-3(1.645))(2.10)-\frac{1}{36}(2(1.645)^{3}-5(1.645))(-0.60)^{2}\)
Substituting the math:
• Skewness Adjustment Component: -0.1706
• Kurtosis Adjustment Component: -0.0428
• Interaction Component: -0.0062
• Resulting \(Z_{CF}\): 1.8646
Notice how the negative skew and high kurtosis pushed the critical multiplier out from 1.645 to 1.8646.
\(\text{Cornish-Fisher\ VaR}=\text{Portfolio\ Value}\times Z_{CF}\times \sigma \)
\(\text{Cornish-Fisher\ VaR}=\$10,000,000\times 1.8646\times 0.015=\mathbf{\$279,690}\)
(For comparison, a standard Gaussian VaR would have completely underestimated this risk at $246,750).

