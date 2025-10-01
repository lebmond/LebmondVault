---
Date: 2024-06-23
tags:
  - SAS
---

> [!Summary] 
> A hash object is an in-memory table that contains key and data components. The hash object provides an efficient, convenient mechanism for quick data storage and retrieval.

# SAS Hash objects
- Hash objects can return multiple values from a given lookup.
- A hash object can be loaded from hardcoded values or a SAS data set, is sized dynamically, and exists for the duration of the DATA step. 
- The hash object is a good choice for ==lookups== that use unordered data that can fit into **memory** because it provides in-memory storage and retrieval and does not require the data to be sorted or indexed. **Only exists at that data step, thus can be space efficient** and **time efficient** (RAM is faster than ROM).
- 即hash object可以作为lookup table,供其他dataset中的某些variable作为hash object的key进行查询
	- 例子: 一个dataset A 中包含员工ID、季度和每个季度的销售额, dataset B建立了一个hash objects, 其key为季度,value为每个季度的目标销售额. 这个例子可以很方便滴查询哪些员工在哪些季度实现了销量.
- Hash object 也可以认为是merge & join的一种方式
## Example Code
```sas
data work.difference (drop = goalamount);
declare hash goal();
goal.definekey("QtrNum");
goal.definedata("GoalAmount");
goal.definedone();

call missing(goalamount);
goal.add(key:'qtr1', data:10);
goal.add(key:'qtr2', data:15);
goal.add(key:'qtr3', data:5);
goal.add(key:'qtr4', data:15);
end;

set sasuser.contrib;
goal.find();
diff = amount - goalamount;
run;
```

## Example: Populated from Existing Data
```sas
data work.info45 work.errors45;
	if _n_=1 then
		do;

			/* use existing dataset from which hash object is populated */
			if 0 then
				set cert.country45;
			declare hash country_table(dataset:"cert.country45");
			country_table.definekey('country_code');
			country_table.definedata('country_name');
			country_table.definedone();
		end;
	set cert.employees45;
	rc=country_table.find(key:country_code);

	/*rc= return code,  results of lookup */
	if rc=0 then	
		/* return 0 if look up is successful. */
		output work.info45;		
	else
		/* return other codes otherwise. */
		output work.errors45;	
run;
```