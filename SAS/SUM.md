 # SAS
## Sample Code
```sas
data output;
	set input;
	summation = sum(variable, summation);
run;

data output2;
	set input;
	summation + variable;
run;
```

这里的两段代码功能完全一样, 第二种是SUM statement的另外一种写法,而不是赋值语句.