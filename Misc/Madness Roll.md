**Madness Roll**  
  
Roll for short, long, or permanent madness, as per the Madness tables in the DMG.  
  
`!madness <short|long|perm>`  
  
```python  
!alias madness embed {{set("name",dict(perm='Permanent',long='Long-Term',short='Short-Term'))}}  
{{set('permmad',get_gvar('a8418394-f45c-4bd7-be80-318eb2bc6835'))}}  
{{set('longmad1',get_gvar('b73224a0-8e56-4fa0-a546-f42561e1ae6b'))}}  
{{set('longmad2',get_gvar('2f0f4277-b0c3-41ba-9efc-e78760f98a8e'))}}  
{{set('shortmad',get_gvar('3e391143-d173-4ce3-823f-f618b3f03bbd'))}}  
{{set("shortmad",(shortmad).split('\n'))}}  
{{set("longmad",(longmad1+"\n"+longmad2).split('\n'))}}  
{{set("permmad",(permmad).split('\n'))}}  
{{set("roll", vroll("1d100"))}}  
{{set("x",ceil((roll.total)/5))}}  
-title "Rolling for {{name["%1%"]}} Madness"  
-f "Roll| {{roll}}"  
-f "Madness|{{%1%mad[x-1]}}"  
-footer "Madness | PHB 259"  
```