---
tags:
  - SAS
  - SQL
---
When you use a column alias in the [[WHERE clause]] to refer to a calculated value, you must use the  [[CALCULATED keyword]] along with the alias.

```SQL
proc sql outobs=10;
	select flightnumber, date, destination,
		   boarded + transferred + nonrevenue as Total
	from sasuser.marchflights
	where calculated total < 100;
```

