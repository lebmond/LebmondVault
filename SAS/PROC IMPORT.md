---
tags:
  - SAS
---
The IMPORT procedure reads data from an **external data source** and writes it to a SAS data set. 
You can import structured and unstructured data using PROC IMPORT:
- delimited files (blank, comma, or tab)
-  Microsoft Excel files

By default, the IMPORT procedure expects the variable names to appear in the first row.
    
- The procedure scans the first 20 rows to count the variables, and it attempts to determine the correct [[SAS informat]] and format for each variable. In addition, you also have the following options:
	-  GETNAMES : modify whether SAS extracts the variable names from the first row of the data set
	- GUESSINGROWS=: indicate how many rows SAS scans for variables to determine the type and length
	- DATAROW=: indicate at which row SAS begins to read the data
	- 
# Sample Codes:
## Sample 1: delimiter
```sas
proc import datafile="/courses/..../class.txt"
dbms = dlm
out = work.class /* The output destination */
replace;
delimiter = '09'x; /* delimited by tab */
run;
```

## Sample 2: One from Multiple Spreadsheet
```sas
PROC IMPORT DATAFILE="/home/u63778763/Data/input105.xlsx"
	DBMS=XLSX
	OUT=RESULTS.JUNE105
	REPLACE;
	SHEET="June"; /*只读入June这张spreadsheet*/
RUN;
```