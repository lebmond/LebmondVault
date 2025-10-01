---
tags:
  - SAS
Date: 2024-04-09
---
# SAS & SQL

SAS can use *[[proc import]]* and *XLSX engine* to import data from **EXTERNAL DATA**, like excel, csv, etc.

SQL are used to import from database.
1. SQL are Structured Query Language, and can be used across many kinds of programming languages or softwares (like Python, , Excel, PowerBI, etc.)
2. In SAS, SQK is built in **PROC SQL**., an interactive procedure that can be run statement by statement until issue the QUIT statement.

# SELECT Statement
## AS Keyword
1. 改名字
	1. 针对select的variable 可以用 as 改名字
```SAS
select country, year as financial_yr from TEMP
where year=2021 and pop > 3000;
```
1. 取名字
	1. 针对新创建的variable 可以用as来取名
## DISTINCT Keyword
```SQL
select distinct country, year from TEMP;
```
distinct 将同时应用到所有被选择的variable上
## CASE ... WHEN Expression
```SQL
select *,
	case
		when degrees > 80 then 'Hot'
		when degrees < 40 then 'Cold'
		else 'Mild'
	end
as Category
from TEMP; 
```

If the when-condition is true for the row being executed, the result-expression following THEN is executed. 
If when-condition is false, PROC SQL evaluates the next when-condition until all where-conditions are evaluated. If every when-condition is false, PROC SQL executes the ELSE expression, and its result becomes the CASE expression's results.
**If no ELSE expression is present and every when-condition is false, the result of the CASE expression is a missing value.**

## [[Where Clause]] AND [[HAVING Clause]]
Used to do subset.

# Set Vertical Combination Using SQL
## Set Operator:
1. INTERSECT: ^bb5df4
	1. Select unique rows that ==are common to both tables==, (to keep duplicate rows from both sets, use [[SQL#ALL|ALL]])
	2. Overlay columns based on their position in the [[SQL#SELECT Statement|SELECT]]  without regarding to the individual column names, **if their type are the same**. To overlay by column names instead of sequence, use [[SQL#CORR|CORR]]
2.  EXCEPT: ^5f5333
	1. Select unique rows from the first table that are not found in the second table (to keep duplicate rows from both sets, use [[SQL#ALL|ALL]])
	2. Overlay columns based on their position in the [[SQL#SELECT Statement|SELECT]]  without regarding to the individual column names, **if their type are the same**. To overlay by column names instead of sequence, use [[SQL#CORR|CORR]]
3. UNION: ^ad9e1f
	1. Select unique rows from ==both== tables (to keep duplicate rows from both sets, use [[SQL#ALL|ALL]])
	2. Overlay columns based on their position in the [[SQL#SELECT Statement|SELECT]]  without regarding to the individual column names, **if their type are the same**. To overlay by column names instead of sequence, use [[SQL#CORR|CORR]]
4. OUTER UNION: ^caabbf
	1. Select all rows from both table(总行数=A行数+B行数)
	   Thus, cannot use together with [[SQL#ALL|ALL]] (as this is already the default behaviour for OUTER UNION)
	2. Do not overlay any columns (总列数=A列数+B列数)
	   When using with [[SQL#CORR|CORR]], 新的列数=A列数+B列数-同名列数
## Keyword
Note that these two keywords can be used together.
### ALL
Does not remove duplicate rows (either duplicate rows in any one of the dataset or duplicate rows across both datasets,说人话就是拼到一起之后再去重)
Cannot be used with [[SQL#^caabbf|OUTER UNION]]
### CORR
Overlays columns by **name** rather than by position (overwrite the defaults for the second behaviour for the set operators)
When used with [[SQL#^5f5333|EXCEPT]], [[SQL#^bb5df4|INTERSECT]], and [[SQL#^ad9e1f|UNION]], removes any columns that are not in both tables.
If an alias is assigned to a column in the [[SQL#SELECT Statement|SELECT]] clause, CORR use the ==alias== instead of the permanent column name.

# Nested Query
## Uncorrelated Subquery
```SQL
select * 
from disk.multiple_financial 
where ID in
	(select ID 
	 from disk.multiple_rating 
	 where df=1 and year=2002);
```
If the subquery returns multiple values and [[SQL#Where Clause AND HAVING Clause|WHERE or HAVING clause]] in the outer query contains a ==comparison== operator that is not modified by ANY or ALL, the query fails.
## Correlated Subquery
A sub-query that uses values **from the outer query**. In this case the inner query has to be executed for **every row of outer query**.
```SQL
select * 
from disk.multiple_financial as a 
where exists
	(select * 
	 from disk.multiple_rating as b 
	 where a.id=b.id and a.year=b.year and b.df=1);
```
Sometimes it is helpful to compare a value with a set of values returned by a subquery.

## Inline View
A special type of nested query that is specified in the outer query's FROM clause. Instead of specifying table name(s) after the **FROM** keyword, the source of the data actually comes from a virtual/temporary table.
### Two advantages
1. We do not need to create the temporary table. This prevents the database from having too many objects, as additional object in the database is costly.
2. Process the code more efficiently.
### Inline View Syntax
```SQL
SELECT a2.ZIP_CODE, COUNT(a1.User_ID)  
FROM  
	(SELECT User_ID, SUM(Score) 
	 FROM User_Score 
	 GROUP BY User_ID 
	 HAVING SUM(Score) > 200
	) a1,  
	User_Address a2  
WHERE a1.User_ID = a2.User_ID  
GROUP BY a2.ZIP_CODE;
```

# Create SAS Macro Variable
```SQL
select count(*) into: frequency 
	from work.overview;
	
select distinct country into: country_list 
	separated by ","
	from work.overview;

%put &country_list.;
```
The generated answer: `Australia,Canada,China,India` 
所有的numeric都变成character
当多个value被generate时:
1. 用`separated`可以形成汇总;
2. 不使用`separated`会仅保留最后一个值到macro中.