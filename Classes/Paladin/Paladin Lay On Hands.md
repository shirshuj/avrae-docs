**Paladin Lay on Hands **  
*By Croebh#5603*  
  
An alias to use the Lay on Hands Paladin class feature. Please set up the CC as per the command, the first one is for Dicecloud, the second for PDFsheet or Gsheet.   
  
To use the lay on hand feature, the command structure is:  
  
`!lay [#|disease|poison]`  
eg. `!lay 8` or `!lay disease`  
  
`!cc create "Lay on Hands" -reset long -max {{5*PaladinLevel}} -min 0`  
`!cc create "Lay on Hands" -reset long -max {{5*level}} -min 0`  
  
```!alias lay embed {{set("a",5 if str("%1%")=="disease" or str("%1%")=="poison" else int("%1%"))}}  
-title "<name> Lays on Hand: {{"FIZZLE" if (get_cc("Lay on Hands") - a)<0 else "Cure Disease" if str("%1%")=="disease" else "Neutralize Poison" if str("%1%")=="poison" else "Heal for "+str(%1%)}}"  
-desc "{{"The lay on hands fails, as they need to have a long rest before channeling again." if (get_cc("Lay on Hands") - a)<0 else str("Their eyes glow white briefly, channeling a sliver of divine energy, as they touch a creature and cure them of a disease.") if str("%1%")=="disease" else str("Their eyes glow white briefly, channeling a sliver of divine energy, as they touch a creature and neutralize a poison afflicting them.") if str("%1%")=="poison" else str("Their eyes glow white briefly, channeling a sliver of divine energy, as they touch a creature and heal them for **"+str(a)+" Hit Points**.")}}" {{"" if (get_cc("Lay on Hands") - a)<0 else (mod_cc("Lay on Hands", -5) if str("%1%")=="disease" or str("%1%")=="poison" else mod_cc("Lay on Hands", -%1%))}}   
-f "Lay on Hands Remaining | {{get_cc("Lay on Hands")}}/{{get_cc_max("Lay on Hands")}}" -thumb <image>```