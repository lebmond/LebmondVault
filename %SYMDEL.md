Use [[%SYMDEL]] statement to delete a macro variable from the ==global== symbol table.
```SAS
%symdel macro_variable;
```

But there isn't a direct way to delete a local macro variable explicitly before the `%mend` statement within the same macro. 
`%SYMEL` cannot delete macro variables from the local symbol table.