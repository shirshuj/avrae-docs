**Arbitrary Tables**  
*By zhu.exe#4211.*  
This alias randomly chooses a result from a table. To set it up, create a cvar with each choice on its own line. To use it, call `!table [cvar name]`. ```  
!alias table echo {{set('choices', %1%.split('\n'))}}{{choices[randint(len(choices))]}}  
```