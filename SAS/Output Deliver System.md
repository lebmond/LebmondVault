---
tags:
  - SAS
Date: 2024-03-17
aliases:
  - ODS
---

> [!summary] 
>Save SAS output to various destinations such as rtf (rich text file, which is word), pdf, csv, csvall, html, etc.

## Sample Syntax
Save the result of PROC FREQ into a html file:
```sas
ods html file="C:\SAS\data\for lecture\output.html"; 
proc print data = overview;
proc freq data = overview;
	tables country; 
run;
ods html close;
```
This outputs **both [[PROC PRINT]] procedure and FREQ procedure** to the output.html.

## Cannot Export to More Than One Destination
