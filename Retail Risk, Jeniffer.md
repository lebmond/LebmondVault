---
tags:
  - GuestLecture
Date: 2024-02-02
---
# Three Primary Financial Risks
[[Operational risk]], Reputational, ESG Risk are non-financial risks

Liquidity mainly focuses on the present value,
Market Risk: between floating and fixed rate mismatches, and term mismatches.

# Credit Modeling
Adjudication: judging wether to issue ==new== loan
Behavioural: more about ==existing== customers
%%PCL%% 
GA: generally allowances, not link to any particular loan
regulatory: focus on extreme loss event
economic: your internal assessment, regardless of regulatory 

# Model Development
Expert: US mortgage an be paid in full, thus when TD entered US market and acquiring small banks, they need the Scoring Vendor to issue score data.

## Logistic Regression
%%LGD: it can also go below or above 100%.... right?%%

%%The reasons to bin the lowest balance within last 6 months? Those whose bank account goes as low as 4999 should have a similar score as those who goes as low as 5000 rather than those of 9999%%

Dist Loans: $$\frac{Number of Loans within a Group}{Total Numbers of Loans}$$, i.e. proportion of total loans
Dist Goods, $$DG_i$$: $$\frac{Number of Good Loans within a i-th Group}{Total Numbers of Good Loans}$$, i.e. proportion of total good loans within each group
	Describe to what extent this group contribute to the good loans
Same for Dist Bads,
	By subtracting Dist Goods and Dist Bads, you can get the significance of distinguishing between good loans and bad loans using this attributes, (i.e. a value that more deviate from 0 is more predictive/ powerful)


%% The whole table and process is doable only if the target is binary, either good or bad loans. Is this the main reason why using these two outcomes without intermediate values"?%%


%% Decision about the information value: subject? in documentation? same across different Characteristic?%%

%%Scoring-Point Scaling? what is a? factor-dependent? if not why not factoring it out%%

## Neural Networks
Historically: each area (market risk, securities, etc.) has their data
Now: satellite database, go to the data stewardess, but you do not know the variable names, and thus have inevitably result in pulling all kinds of different variables (that do not have apparent relationships or at least you do not know). Each time you recalibrate these variables can change.

Neural networks: may result in a model that is not deployable (final variables the model is using must be real-time data, but in reality these data might go through pipelines using years) , because you cannot generate an executable file. 