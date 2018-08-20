**Wild Shape Attacks**  
*By 181128299659919360 *  
  
A series of aliases to change various attacks for wild shape purposes. You can add other aliases like `!bear` to change the stats further.  
  
```py  
!alias wolf embed  
{{set_cvar("SSattack1", "Bite")}}  
{{set_cvar("SSAtkrl1", "1d20+5")}}  
{{set_cvar("SSdmgrl1", "2d6+3[piercing]")}}  
{{set_cvar("SSimage", "https://imgur.com/tTOAhRt.png")}}  
-title "<name> Shapeshifts into a ferocious Dire Wolf!"  
-desc "{{"She gains the following attack: \n"+str(SSattack1)+" with "+str(SSAtkrl1)+" chance to hit for "+str(SSdmgrl1)+" damage"}}"  
```GN  
```py  
!alias satt1 embed -desc "<name> makes a **{{(SSattack1)}}** attack" -f "Attack: |  
**To Hit:**  {{vroll(SSAtkrl1)}}  
**Damage:** {{vroll(SSdmgrl1)}}"  
-color "#FF0000"  
-thumb "{{(SSimage)}}"  
```