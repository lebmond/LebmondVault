# SAS SORT
```sas
PROC SORT DATA = INPUT OUT = WORK.OUTPUT;
by Variable1 descending Variable2;
run;
```
按照Variable1从小到大、Variable2从大到小排序.