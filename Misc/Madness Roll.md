**Madness Roll**  
  
Roll for short, long, or permanent madness, as per the Madness tables in the DMG.  
  
`!madness <short|long|perm>`  
  
```python  
!alias madness embed {{g,r,t=load_json(get_gvar('fa0c87b9-44cc-41b1-9d5c-0a424ba058ba')),vroll('1d100'),'&*&' if '&*&' else 'short'}}{{R=(r.total+4)//5}}
{{v=t in 'short long indefinite'}}{{t='short' if t in 'short' else 'long' if t in 'long' else 'indefinite'}}
-title "{{f"Rolling on the {t.title()}{'-Term' if t!= 'indefinite' else ''} Madness table!" if v else "Error, invalid input"}}"
-desc "{{[g[t][i].desc for i in range(len(g[t])) if R in g[t][i].index][0] if v else 'Table not found.\nPlease try `short`, `long`, or `indefinite`.'}}"
{{f"-f 'Madness Roll|{r}'" if v else ''}}
-footer "Madness | DMG 259" -color <color>
```
