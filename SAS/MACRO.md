---
tags:
  - SAS
Date: "240302"
---
# Idea of MACRO statement: 
automation and efficiency
# Macro Variable
## Define Macro Variable
1. %LET Statement
```SAS
	%let i=10;
```
2. [[CALL SYMPUT]]
   
> [!attention] 
> Need to provide a **character string** as the name for the macro variable, and then assign a SAS **variable**'s value to it.

3. [[SQL#Create Macro Variable|SQL Method]]

## Resolve Macro Variable
### Resolve as Values
```sas
   %let data=work.overview; /* define a macro variable;*/
   proc print data=&data; /*use & to resolve it; */
   /*double quotes "" - resolve macro variable;*/
   title "A listing of the &data SAS data set";
   /*single quotes '' - not resolve macro variable;*/
   title2 'A listing of the &data SAS data set';
   run;
```

打印的标题如下:
Using double quote: A listing of the cert.Overview SAS data set
Using single quote: A listing of the &data SAS data set
	
```sas
	%let i=10; /*what if I want resolve "i" in "ith";*/
	proc print data=cert.overview(obs=&i firstobs=&i);
	/**resolved as 10th;*/
	title "&i.th Record in work.overview"; 
	/*can not resolve; ith is not a macro variable;*/
	title2 "&ith Record in work.overview"; 
	run;
	title;

	%put &data &i;
```

&i.th: "." is the separator here so that SAS can recognize that the [[MACRO]] variable's name is i rather than ith.
### Resolve to Log
[[%PUT]] statement can put resolutions into SAS's LOG window.
### Consecutive Amerpsands
This technique force multiple reads of a macro variable reference by the macro processor. More about this technique can be found through https://support.sas.com/resources/papers/proceedings/proceedings/sugi29/063-29.pdf
#### Rules for consecutive resolving:
1. Resolves left to right;
2. `&&` will be resolved as `&`;
3.  In each read, SAS only resolve each `&` (or each `&&`) once;
4. SAS repeatedly reads until all `&` are resolved.
#### Examples
```SAS
%let a=alpha;
%let b=beta;
%let abeta = pair;

%put &a&b;   /*resolve to alphabeta*/
%put &&a&b;  /*resolve to pair*/

%let attri=name;
%let name=shan;
%let shan=chinese;

%put &name is a &&&&name; /*shan is a shan*/
%put &name is a &&&&&name;/*shan is a chinese*/
%put &name is a &&&&&&name;/*shan is a chinese*/
```
## Delete Macro Variable
Use [[%SYMDEL]] statement to delete a macro variable from the **global** symbol table.
# Macro Functions
Macro functions are used to handle Macro variables:
1. [[%eval]]
2. [[%sysevalf]]
3. [[%sysfunc]]

## MACRO Condition
Can only be used within macros definitions.
```SAS
%macro macro32;
	%if expression %then %do;
		SAS Code;
	%end;
	%else %do;
		SAS Code;
	%end;
%mend;
```
## MACRO ITERATION
Can only be used within macros definitions.
### Example: To By
```sas
%macro macro33;
	%do macro_variable = start %to stop <%by increment>;
	SAS code;
	%end;
%mend;
```
Notice the **Initialization of the Loop Variable:** `macro_variable` is used directly without the preceding `&`.
### Example: While
```sas
%macro macro34;
	%global x;
	%let x = 1.25;
	%do %while(&x <= 2):
		%put &x;
		%let x = %sysevalf(&x + 0.25);
	%end;
%mend;
```
### Example: Until

```Sas
%macro macro34();
	%global x;
	%let x = 1.25;
	%do %until (%sysevalf(&x = 2));
		%put &x;
		%let x = %sysevalf(&x + 0.25);
	%end;
%mend;
```

### Explanation
`%sysevalf` is used for arithmetic calculations on floating-point numbers in macro expressions. It evaluates the expression and updates `x` with the new value.
`%eval`  can lead to incorrect results due to round-off errors.

## Automatic MACRO Variable
Automatic macro variables contain information about your ==computing environment, such as the date and time of the session, and the version of SAS that you are running==.
- Created when SAS is invoked
- Global (always available)
- Assigned values by SAS/User
### Fixed Value

| Name     | Value                                                                                                                                                          |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SYSDATE  | the date of the SAS invocation (DATE7.)                                                                                                                        |
| SYSDATE9 | the date of the SAS invocation (DATE9.)<br>                                                                                                                    |
| SYSDAY   | the day of the week of the SAS invocation                                                                                                                      |
| SYSTIME  | the time of the SAS invocation                                                                                                                                 |
| SYSENV   | FORE (interactive execution) or BACK (noninteractive or batch execution)                                                                                       |
| SYSSCP   | an abbreviation for the operating system that is being used, such as WIN or LINUX                                                                              |
| SYSVER   | the release of SAS that is being used                                                                                                                          |
| SYSJOBID | an identifier for the current SAS session or for the current batch job (the user ID or job name for mainframe systems, the process ID (PID) for other systems) |
### Auto-Updated Value
Some automatic macro variables have values that automatically change based on submitted SAS statements.

| Name    | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SYSLAST | the name of the most recently created SAS data set, in the form LIBREF.NAME. This value is always stored in all capital letters. If no data set has been created, the value is _NULL_;<br>Note:Throughout this book, the keyword _NULL_ is often used in place of the data set name in sample programs. Using _NULL_ suppresses the creation of an output data set. Using _NULL_ when benchmarking enables you to determine what resources are used to read a SAS data set. |
| SYSPARM | text that is specified when SAS is invoked                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| SYSERR  | contains a return code status that is set by the DATA step and some SAS procedures to indicate whether the step or procedure executed successfully                                                                                                                                                                                                                                                                                                                          |
