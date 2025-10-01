---
tags:
  - SAS
Date: 2024-02-17
---
# SAS
From a SAS date value, returns an integer that corresponds to the day of the week.
## Syntax
WEEKDAY( [expression](https://documentation.sas.com/doc/en/vdmmlcdc/8.1/ds2ref/p0gjyqp85484vpn1cnz3prseelxb.htm#p18fdq5krtikuqn18ci1os9jo21w))
### Arguments
#### expression
specifies any valid expression that represents a SAS date value.
### Return Data Type

|           |                                                                                                                                                 |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Data type | DOUBLE                                                                                                                                          |
| See       | [DS2 Expressions](https://documentation.sas.com/doc/en/vdmmlcdc/8.1/ds2pg/p0x72z9nojd1djn1rfa5gfapkrkg.htm) in SAS Viya: DS2 Programmer’s Guide |

## Details

The WEEKDAY function produces an integer that represents the day of the week, where 1 = Sunday, 2 = Monday, …, 7 = Saturday.