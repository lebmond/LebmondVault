---
tags:
  - SAS
Date: "240214"
---
```sas
data overview;  /* to generate a new data set called overview */
  infile cards; /* read in a file starting from cards statement */
  length country$30;
  input Country$ Year gdp pop;  /* read in those variables, use $ to make it a character variable*/
  cards; /*indicate start of the actual data*/
Canada 2007 87943 1900
Canada 2006 89345 1876
Canada 2005 97712 1873
Australia 2007 85711 2412
Australia 2006 91028 2356
Australia 2005 101124 2342
China 2007 146018 11948
China 2006 151337 11542
China 2005 152035 11182
India 2007 64269 9023
India 2006 63558 8943
India 2005 62854 8876
; 
run;
```

使用该方法读入variable 的default length: 8bytes
1. numerical: $2^{32}-1$
2. character: 8个字符
3. 可以用length Variable_name$30; 手动分配30bytes的空间