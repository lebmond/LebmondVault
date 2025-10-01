---
tags:
  - SAS
  - Macro
Date: 2024-06-19
---
Create macro variables that contain the **values of variables** from **SAS dataset**. But you cannot resolve them in the same data step.
即批量建立macro variable.
## Syntax
CALL SYMPUT(_macro-variable_, _value_);
### Required Arguments
#### _macro-variable_
can be one of the following items:
- a ==character string== (must be a [[SAS Name]])enclosed in quotation marks. For example, to assign the character string `testing` to macro variable *NEW*, submit the following statement:
    ```sas
    call symput('new','testing');
    ```

> [!attention] 
> Need a character string as the macro name

- the name of a character ==variable==, whose values are [[SAS Name|SAS names]]. For example, this DATA step creates the three macro variables SHORTSTP , PITCHER, and FRSTBASE and respectively assign them the values ANN, TOM, and BILL:   ^9a7a52
    ```sas
    data team1;
       input position : $8. player : $12.;
       call symput(position,player);
    datalines;
    shortstp Ann
    pitcher Tom
    frstbase Bill
    ;
    ``` 
- a character expression that produces a macro variable name. This form is useful for creating a series of macro variables. For example, the CALL SYMPUT statement builds a series of macro variable names by combining the character string POS and the left-aligned value of _N_ . Values are assigned to the macro variables POS1, POS2, and POS3.
    ```sas
    data team2;
       input position : $12. player $12.;
       call symput('POS'||left(_n_), position);
       datalines;
    shortstp Ann
    pitcher Tom
    frstbase Bill
    ;
    ```
#### _value_
is the value to be assigned, which can be
- a string enclosed in quotation marks. For example, this assigns the string `testing` to the macro variable NEW:
    ```sas
    call symput('new','testing');
    ```
- the name of a numeric or character variable. The current value of the variable is assigned as the value of the macro variable. 
	- If the variable is numeric, SAS performs an automatic numeric-to-character conversion and writes a message in the log. 
		- Later sections on formatting rules describe the rules that SYMPUT follows in assigning character and numeric values of DATA step variables to macro variables.
	- Note: most useful when _macro-variable_ is also the name of a  variable. A unique macro variable name and value can be created from each observation, as shown in the [[CALL SYMPUT#^9a7a52|previous example]].
	- If _macro-variable_ is a character string, SYMPUT creates only one macro variable, and its value changes in each iteration of the program. Only the value assigned in the last iteration remains after program execution is finished.
- a DATA step expression. The value returned by the expression in the current observation is assigned as the value of _macro-variable_. In this example, the macro variable named HOLDATE receives the value `July 4,1997`:
    ```sas
    data c;
       input holiday mmddyy.;
       call symput('holdate',trim(left(put(holiday,worddate.))));
    datalines;
    070497
    ;
    run;
    ```
    If the expression is numeric, SAS performs an automatic numeric-to-character conversion and writes a message in the log. Later sections on formatting rules describe the rules that SYMPUT follows in assigning character and numeric values of expressions to macro variables.

## Example 1
```SAS
/* Create the dataset */
data overview3;
input Record_No gdp;
datalines;
1 3000
2 5000
3 4500
;
run;

data _null_;
	set overview3;
	call symput(cats('Record',Record_No), gdp);
run;
```
### Explanation
1. **`data _null_;`**: This initiates a data step that doesn't create an output dataset.
    
2. **`set overview3;`**: This reads data from the `overview3` dataset.
    
3. **`call symput(cats('Record', Record_No), gdp);`**:
    - `cats('Record', Record_No)` uses [[cats]] concatenates the string 'Record' with the value of `Record_No` to dynamically create macro variable names (`Record1`, `Record2`, etc.).
    - `gdp` is the value that will be assigned to each macro variable.
4. **`run;`**: This statement ends the data step.
## Example2
```sas
data _null_;
set overview3;
if _n_ =1 then call symput("Record",gdp);
run;
```
## Example  3
```sas
data _null_;
set overview3;
call symput("line"||compress(_n_),put(gdp,dollar10.1));
run;
```
### Explanation
1. **`call symput("line"||compress(_n_), put(gdp, dollar10.1));`**:
    - `"line"||compress(_n_)`: This part concatenates the string "line" with the iteration number `_n_` (automatically provided by SAS as the data step loops through each row). The `compress` function is used here, although it's not necessary unless you're trying to remove spaces or other characters from `_n_` (which by default doesn't have any). The correct usage would just be `"line"||_n_` if `_n_` is only numeric.
    - `put(gdp, dollar10.1)`: This function converts the numeric `gdp` variable into a formatted string with a dollar sign and one decimal place. For example, a `gdp` of 1000 would be formatted as `$1,000.0`.
### Result
- `&line1` would be `$1,000.0`
- `&line2` would be `$2,000.0`
- `&line3` would be `$3,000.0`