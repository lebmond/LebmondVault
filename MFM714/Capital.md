---
tags:
  - MFM714
Page: "48"
Date: 2024-01-24
---
> [!NOTE]Description
> Bank capital is the net value of a company that the shareholders have in the firm, absorbing unexpected loss.

- Definition:
    - Book Value Way: Represents the difference between a bank's assets and liabilities.
    - Market Value way:  Present value of future earnings. 
        - Corporation being public is one reason for market value to be higher than the book value (the market value contains the discounted potential future cashflow)
    - Difference between Book Value and Market Value is recognized as goodwill when corporation/firm is bought out.
        - Bank capital consists of various components, including common equity, retained earnings, and additional paid-in capital. Regulatory authorities set minimum capital requirements for banks to ensure their financial stability and ability to withstand adverse events.
        - Unlike reserves, which are primarily used for liquidity management, bank capital is a long-term source of funding that supports a bank's ongoing operations and growth.
    - 
- Categories (Non-mutually exclusive)
	- ==Economic Capital==: required capital level determined by **bank risk management department internally**. Quants try to produce the unexpected loss distribution and figure out the bank's VaR or ES level, and maintain the capital at that level to achieve their desired PD.
	- ==Regulatory Capital==: amount set by **regulators**(OSFI in Canada) to ensure the safety of the whole system
		- e.g. During the crisis, RBC and TD had to issue new shares to increase their capital even though they had enough according to economic capital and regulatory capital calculations.
		- Further divided into:
			- [[Common Equity Tier 1 Capital]]
			- [[Additional Tier 1 Capital]]
			- [[Tier 2 Capital]]
			- etc.
	- ==Rating Agency Capital==: the amount of capital so that the firm can achieve their desired credit rating offered by the rating agency
- These capital are overall capital level assessment, and an allocation down to lower level is needed.

# Quantifying Capital Needed
- 99% VaR or CVaR($E[-\Delta P(t)\big|-\Delta P>VaR_{99\%}]$)