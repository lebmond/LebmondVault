---
Date: 2024-06-23
tags:
  - SAS
---

> [!Summary] 
> Array assigns aliases for a series of variables and allows you to loop among variables

1. Name of the array must be a [[SAS Name]] that cannot be the name of the variable in the same data set or the name of a SAS function.
2. Name of the array exists only for the duration of the DATA step, while cannot be used in the PROC step (array是逻辑上的临时alias分组而非永久的数据实例)
3. Array name cannot be used in the data set option, keep/drop statement or other statement
## Syntax
```sas
array array_name (number) $w variable_names (initial_values);
```
`Number` can be either a number or * so that the length would be automatically determined. 
After setting up an array, the number of elements in an array can be returned by [[DIM Function]]. Note that `fruit(3:5)` will create array with 3 elements. 
`$w` is used to define character array and can be omitted. Note that `w` should be replaced by a number (e.g. `$8`)
### Example
```sas
array sales{1:3} MondaySales TuesdaySales WednesdaySales;
array newArray{*}  $2 x1-x4 ("A", "B", "C", "D");
array ratingArray{5};
```
#### Example 42
Open a new programming window to create ACT42.sas in `C:\cert\programs`. Write a SAS program that will use arrays to convert character test score to numeric test score values.
- Use a SAS DATA step to create data set work.ACT42 from cert.answers42.
- Create the CharAnswer array to reference the variables Q1 through Q10 (10 variables).
- Create the NumAnswer array to create the variables NumAnswer1 through NumAnswer10 (10 variables).
- Within a DO loop, map the values of the CharAnswer variables to numeric values as follows:
  A-->1 B-->2 C-->3 D-->4 E-->5
##### dumb way
```sas
data work.act42;
set cert.answers42;
if Q1 = 'A' then NumAnswer1=1;
if Q1 = 'B' then NumAnswer1=2;
if Q1 = 'C' then NumAnswer1=3;
	...
if Q2 = 'A' then NumAnswer2=1;
if Q2 = 'B' then NumAnswer2=2;
if Q2 = 'C' then NumAnswer2=3;
	...
run;
```
##### ARRARY way
```sas
data work.act42;
set cert.answers42;
array CharAnswer(10) Q1-Q10;
array NumAnswer(10) NumAnswer1-NumAnswer10;

do i=10 to 10;
	if CharAnswer(i) = 'A' then NumAnswer(i) = 1;
	else if CharAnswer(i) = 'B' then NumAnswer(i) = 2;
	else if CharAnswer(i) = 'C' then NumAnswer(i) = 3;
end;

drop i;
run;
```

### Multi-Dimensional Arrays
```SAS
array array_name {dimension1, dimension2, ...};
```