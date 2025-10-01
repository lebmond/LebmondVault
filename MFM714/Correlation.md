---
tags:
  - MFM714
Date: "240115"
Page: "15"
---
Used to determine how the changes in credit quality of one asset affect the credit risk of other assets, and further affect the overall portfolio credit risk.

# Three Approaches to Characterize Correlation
## Correlate Normalized Asset Returns
**Favoured credit risk management approach**, referred to as a ==structural model==, borrowed from [[Merton Model]]:
	Default occurs when assets' value falls below a default threshold. 
It's noteworthy that the threshold for a higher-rated company is also higher.
The normal PDF and transition matrix is used to characterize the region of default. 

## Principal Component Analysis
As we perform the eigenvalue decomposition on variance-covariance matrix $\Sigma=[Cov(i,j)]$, the greatest eigenvectors in succession are the first, second, and third components for the correlation matrix. Their changes are represented by yield curves' parallel movements, yield curves' steepness, and yield curves' curvature, respectively. 
Then the linear combination of first several components (i.e. the eigenvectors) with random weights represent the changes of yield curve. The sum of their corresponding eigenvalues represents the total variance of these changes in yield curve.

## CAPM style
Assume the existence of one global systemic risk, $\epsilon_0$, and idiosystemic risk that is independent across all assets, $\epsilon_i$. Thus, we can write the variance of any asset to be the linear combination of systemic risk and idiosystemic risk such that variance of any asset is 1. And thus, the correlation between any two assets, $X_i$ and $X_j$ is calculated as the product of their corresponding systemic risk weights ($\rho_{i,j}=q_iq_j$ ).


> [!NOTE] Title
> Linked each company with the global factor, and through this factor establish their correlation


In practice, we select an index as the proxy for the systemic variable.
## Creditmetrics
More like a two-layer CAPM approach. Characterize the normalized asset return of $i^\text{th}$ corporation by :$$x_i=p_iy_j+\sqrt{1-p_i^2}z_i$$ where $z_i$ is an independent $N(0,1)$ random variable representing **idiosyncratic changes specific to $i^\text{th}$ corporation**,  and $y_i$ is a random variable representing changes within the entire $j^\text{th}$ industry. 
Then, $$y_i=q_j\xi_0+\sqrt{1-q^2_j}\xi_I$$where systemic risk, $\xi_0$ and idiosystemic risk specific for each industry $\xi_I$. Thus, the correlation between two asset return is now the product of their own company-specific risks, and their industry-level systemic risks.
### Assumptions:
1. Credit status transitions are characterized and only characterized by credit rating changes;
2. Empirical probabilities are indicative of the underlying true probabilities;
3. Same probability of transition for a certain credit rating.

### [[Correlation]]s
Correlation are based on the firm's industry classification and size.
- Typically, the larger firms are attributed the larger correlations.
- The highest observed correlations tend to arise for larger banks within the same country.

> [!NOTE] Title
> Link them directly


### Beta
More of the business people notion. Not the $q$ within the CAPM model, it is more like the volatility.




$$
S_t=S_0exp\{(r-\frac{1}{2}\sigma^2)\tau\}exp\{\sigma\sqrt\tau\xi\}
$$