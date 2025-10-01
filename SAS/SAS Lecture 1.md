---
tags:
  - SAS
Date: 2024-02-14
---
# Variable
Variable 类型:
1. numerical: 只能存数字
2. chracter: 能储存数字、字母、符号

使用[[INFILE CARDS]]读入数据
使用[[PROC IMPORT]]从外部数据

## [[SAS Name]]

```
## Label
除了命名以外的、对变量的名字, 但是只是美观目的(打印的时候才显示),在写码时候还是得用variable names

# Structure of SAS Program
1. step: 一段code
	1. data step
		1. 目的: prepare dataset, 
		2. create a new dataset update existing dataset
	2. proc step
		1. 分析、处理、展示、建模
2. statement: 一句code
	1. Data statement:
		1. 包含在data step中的所有statement
	2. Proc Statement:
		1. 包含在proc step中的所有statement
	3. [[Global Statement]]:
	4. [[MACRO]] Statement:
		1. 宏
3. option: 一个关键词
	1. global option 全局关键词 (start with OPTIONS as if it is a statement)
		1. 举例:
			1. PAGESIZE
			2. NONUMBR
			3. [[NOCENTER]]
	2. dataset option 
		1. 使得程序看起来更简洁:
		2. 举例
		   以下两段代码是等价的
```SAS
data work.temp;
SET overview;
KEEP country year pop; /*drop gdp;*/ 
RENAME pop=population;  
WHERE country='China';  
LABEL year="Fiscal Year"; /*Modify how the column name is printed*/
run;

data work.temp;
set overview (keep = country yr pop 
              rename = (yr = year pop = population)
              where = (country = 'China'));
LABEL year = "Fiscal Year";
run;
```
		这里的keep, rename, where都是 Option