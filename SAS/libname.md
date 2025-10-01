---
tags:
  - SAS
---
1. 设定新的library
   ```SAS
   *libname statement set up a library for permanent SAS data set or excel workbook, will discuss immediately in the next topic; 
   libname saslib "path of the library";  
   libname qtrdata "qtr1.xls";
```

## Read Excel Data with XLSX Engine
   ```sas
   libname library_name XLSX "This_is_a_path/a.xlsx";
```

^1f072f

	This code reads using XLSX engine. Notice that all the spread sheets will be disbursed into different datasets individually. 