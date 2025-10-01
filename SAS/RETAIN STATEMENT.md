---
tags:
  - SAS
Date: 2024-03-17
---
# SAS
> [!summary] 
> Preserve a variable’s value from the previous iteration of the DATA step.

- The RETAIN statement can appear anywhere in the DATA step, it is more efficient than the assignment statement, because it will be executed only once (declarative).
  ## Syntax
  If not specifying initial value, then initialize the variable list with **missing**: 
```sas
RETAIN variable_list;
RETAIN variable_list initial_value;
```
## Example
```sas
data coins;
infile year quantity;
retain tot_quantity 0;
tot_quantity = tot_quantity + quantity;
/*tot_quantity = sum(tot_quantity, quantity);*/
run;
```

Note that using *tot_quantity = tot_quantity + quantity;* can be problematic due to missing values. Use [[SUM]] is a better approach (but you use it for the special cases where you simply want to **cumulatively add** the value of an expression to a variable).
## Relate
1. Another [[SUM]] does not involve [[RETAIN STATEMENT]]: 
   ```sas
   data coins;
   infile year quantity;
   retain tot_quantity 0;
   tot_quantity + quantity;
   run;
```
2. Can also use PROC MEANS to cumulatively add:
   ```sas
   proc means data = WORK.MY_DATA sum;
   vars = A_VAR_TO_BE_ADDE;
   run;
   ```