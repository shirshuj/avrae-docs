**Trinket Roll**  
  
Roll for a random trinket as per the PHB.  
  
`!trinkroll`  
  
Cvars - <https://pastebin.com/eCdRFREN>  
  
```python  
!alias trinkroll embed {{set("trinket",(trinket1+"\n"+trinket2+"\n"+trinket3).split('\n'))}}  
{{set("roll", vroll("1d100"))}}   
-title "Rolling for a Trinket!"   
-f "Roll | {{roll}}"   
-f "Trinket| {{trinket[roll.total-1]}}"   
-footer "Trinkets | PHB 159"  
```