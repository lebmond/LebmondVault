---
tags:
  - SAS
Date: 2024-02-17
---
# Data
## SAS Data: Dataset
sufix: sas7bdat
1. Type:
	1. temporary library: WORK
		1. WORK.Overview: 在temporary library中创建一个叫做Overview的SAS DATASET.
		2. WORK可省略(即WORK.OVERVIEW和OVERVIEW等价)
	2. permeant library
2. They can be loaded into SAS using SQL.

## External Data
excel, csv, txt, etc.
1. USE [[PROC IMPORT]] to load them into SAS as a dataset.
2. USE [[libname#^1f072f|XLSX Engine]] to load multiple XLSX spreadsheets from Microsoft Excel into SAS.

## Missing data
- Numeric missing is presented as a period (.); 
- character missing is presented as blank 
- Missing data is less than any other valid values  
    - SAS will treat as missing numeric value if it encounters:
- Generation of Missing data:
	1. an invalid numeric data (for example, letters)
	2. division by zero (5/0 = missing)  
	3. performing an operation on missing value (1+missing = missing)

## SAS Date
-  A special numeric data, representing the the **number of days** between a specific date and January 1, 1960.
- SAS date constant: “ddMMMyyyy”d  
    Example: 
	- "01Jan1960"d = 0,
	- “02Jan1960”d = 1, 
	- "01Jan1961”d = 366
-   Date related statements:
	- [[WEEKDAY]] STATEMENT
	- QTR STATEMENT
	- DATE/TODAY STATEMENT
	- DATETIME STATEMENT

# Practice
The following SAS program is submitted: 
```sas
data work.january; 
set work.allmonths (keep = product month num_sold cost); 
if month = 'Jan' then output; 
sales = cost * num_sold; 
drop = product num_sold; 
run; 
```

Which variables does the WORK.JANUARY data set contain? 
	A. SALES only 
	B. MONTH, NUM_SOLD and COST only 
	C.SALES, MONTH, NUM_SOLD and COST only 
	D. An incomplete output data set is created due to syntax errors
Correct: D, drop is an assignment statement, thus a syntax error will be casted,