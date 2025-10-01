---
Date: 2024-06-19
tags:
  - SAS
---
This functions allows ==integer== arithmetic of macro variables. Decimal points are not allowed in expression
Does not permit non

```SAS
%let expression1 = 5/3;
%let expression2 = %eval(5/3);
%let expression3 = 0.5 * 2;

%put &expression1.;  /*   5/3 */
%put &expression2.;  /*   1   */
%put &expression3.;  /* Invalid*/
```