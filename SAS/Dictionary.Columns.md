---
Date: 2024-06-25
tags:
  - SAS
aliases:
  - sashelp.vcolumns
---
A SAS dictionary that contains all information about variables and their attributes.

For example, the [[Dictionary.Columns]] table contains information (such as name, type, length, and format) about ==all columns in all tables== that are known to the current SAS session.

## Example

| libname | memname | memtype | name | type | length | npos | label | format |
| ------- | ------- | ------- | ---- | ---- | ------ | ---- | ----- | ------ |
|         |         |         |      |      |        |      |       |        |

- libname: 在哪个library(逻辑库)
- memname: short for "member name", dataset的名字
- name: variable name
## Usage
Here below is a SQL query listing the tables from the ORION library containing column names that end with "Date"
```sql
select distinct memname 'Tables'
	from dictionary.columns
	where libname = 'Orion'
		and name like '%Date';
```