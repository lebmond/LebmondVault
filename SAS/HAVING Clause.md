---
tags:
  - SAS
  - SQL
---

> [!summary] 
> The Having Clause allows you select out **certain groups** based on their summary values.

```SQL
SELECT country, min(GDP)
	FROM work.demo
	WHERE pop > 2400
	GROUP BY country
	HAVING count(*) >= 2;
```

## Having Clause & [[Where Clause]] Contrast
1. [[Where Clause]] chooses observations, and HAVING clause chooses groups;
2. [[Where Clause]] is executed prior to HAVING Clause.
3. [[WHERE Clause]] needs [[CALCULATED keyword]] but HAVING clause does not.