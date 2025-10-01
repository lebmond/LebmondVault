---
tags:
  - SAS
Date: 2024-03-01
---
Every time an output statement is hit the current record is saved to the output data set.
If a data step has no OUTPUT statement then there is an implied OUTPUT at the end of the data
If the data step contains one or more OUTPUT statements then there is no longer an OUTPUT implied at the end of the data step

OUTPUT 后面可以指定输出的dataset:
```sas
data work.beds(keep=Actual Year TotalBed)
	 work.sofas(keep=Actual Year TotalSofa);
	 
	 set cert.input104;
	 if product='BED' then do;
	 	TotalBed+Actual;
	 	OUTPUT work.beds;
	 	end;
	 else if product="SOFA" then do;
	 	TotalSofa+Actual;
	 	OUTPUT work.sofas;
	 	end;
run;
```