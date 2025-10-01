---
Date: 2024-06-25
tags:
  - SAS
---
> [!Summary]
> Dictionary tables are commonly used to monitor and manage SAS sessions. 

1. Dictionary tables are special, ==read-only== SAS tables that contain information about SAS libraries, SAS macros, and external files that are in use or available in the current SAS session.
2. Dictionary tables also contain the settings for SAS system options and SAS titles and footnotes that are currently in effect.

## [[Dictionary.Columns]]

## View 形式
1. 每次被referenced的时候才会响应、然后当即更新(created each time they are referenced in a SAS program)
2. updated automatically
3. limited to Read-Only Access

