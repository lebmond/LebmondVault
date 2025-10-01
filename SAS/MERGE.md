---
Date: 2024-03-17
tags:
  - SAS
---
# Merge 概述
## Four Merge Types
Can be freely selected by the users according to their needs.
Define three sets:
A: all data items in and only in *dataset1*
B: all data items in and only in *dataset2*
C: all data items both in *dataset1* and *dataset2*

1. inner join: $C$
2. left join: $A+C$
3. right join: $B + C$
4. full join: $A+B+C$

Here left join, right join, and full join together are called **outer join**.
## Three Merge Relationships
Determined by the key values (or the dataset itself). You cannot freely select between these options.
1. One-to-One Merge: unique key in both datasets
2. One-to-Many Merge: unique key in *datasetA* to non-unique key in *datasetB*
3. Many-to-Many Merge: non-unique key in *datasetA* to non-unique key in *datasetB*. Cannot be done in SAS MERGE statement but can be done in SQL.

# SAS Merge

## Sample Code
### Sample 1
```sas
DATA output_dataset;
merge SHEET1(in = idx_1) SHEET2(in = idx_2);
BY VARIABLE_LIST; /* the key value for merge) */
IF idx_1 = 1; /* left_join */
/*IF idx_2 = 1;  right_join*/
/*IF idx_1 = 1 and idx_2 = 1;    inner_join*/
/*IF idx_1 = 1 or idx_2 = 1;     full_join*/
RUN;
```

### Sample 2
```sas
data WORK.ALL;
merge WORK.EMP_NAME(in = Emp_N)
	  WORK.EMP_DEPT(in = Emp_D);
by Empid;
if (Emp_N and not Emp_D) or (Emp_D and not Emp_N);
run;
```
这一段代码保留了同时仅在EMP_NAME和EMP_DEPT出现的行
## 注意事项
1. Key variable column should be sorted before call MERGE.
2. Key variable's name must be identical (cannot merge the *amount* to *amt*)
3. Do not perform [[many-to-many merge]] in data steps (but can be done in SQL)
	1. can use DUP to check if the key variable column is unique.

# SQL Merge
When [[MERGE#Four Merge Types|any type of merge]] is processed, PROC SQL starts by generating the [[Cartesian Product]] which contains all possible combinations of rows from all tables.

### Left Join Example
```SQL
create table work.info45 as 
	select a.*, b.country_name 
	from cert.employees45 as a 
		left join cert.country45 as b 
	on a.country_code=b.country_code 
	where country_name is not missing;

create table work.errors45 as 
	select a.*, b.country_name 
	from cert.employees45 as a 
		left join cert.country45 as b 
	on a.country_code=b.country_code 
	where country_name is missing;
```

# Merge using [[Hash Object]]
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