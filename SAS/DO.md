---
tags:
  - SAS
Date: 2024-03-01
---
# DO Group
逻辑上的大括号, enclose multiple statements
```sas
data do_group;
	set cert.Overview;
	if country="China" then do;
		FX=0.2; 
		output;
	end;
	else if country="Canada" then do;
		FX=1;
		output;
	end;
run;
```

# DO Loop
Two identical statements:
```sas
DO i = 1 to 20 by 1;
DO i = 1 to 20;

/*Do while statement*/
DO WHILE (PD LE 0.5);
DO UNTIL (PD GE 0.5);
```
[[Comparison Operators]] is given here.