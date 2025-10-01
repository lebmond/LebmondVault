---
Date: 2024-06-18
tags:
  - SAS
---

> [!summary] Summary
> Used to subset certain rows from the underlying dataset.

In the where clause, can specify any column(s) from the underlying table(s). The columns specified in the WHERE clause do not have to be specified in the SELECT clause.

When you use a column alias in the WHERE clause to refer to a calculated value, you must use the  [[CALCULATED keyword]] along with the alias.
```SQL
SELECT *
FROM Work.Demo
WHERE Salary is not missing;
quit;
```