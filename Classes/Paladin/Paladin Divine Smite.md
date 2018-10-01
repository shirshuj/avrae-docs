**Paladin Divine Smite **  
*By Croebh#5603*  
  
An alias to use the Divine Smite Paladin class feature. Use the first argument `[level]` to denote what spell slot you'd like to spend, and then for the second argument, say crit if its critical, or blank if its not. Uses the appropriate spell slot, displays your slots left, and fizzles if you don't have a slot available. Maxes out at 5d8, or 10d8 if its a crit.  
  
`!smite [level] [crit]`  
eg `!smite 2` or `!smite 1 crit`  
  
```py  
!alias smite embed   
{{set("z",1 if "%2%"=="crit" else 0)}}  
{{set("x",get_slots(%1%))}}   
{{set("w", (((%1%+1) if int(%1%) < 4 else 5) * 2 if z==1 else ((%1%+1) if int(%1%) < 4 else 5)))}}  
{{set("y", vroll(str(w)+"d8[radiant]"))}}  
-title "<name> {{"attempts to channel" if x==0 else "channels"}} a {{"CRITICAL " if z==1 else ""}}level %1% Divine Smite!"   
-desc "Their weapon {{"sparkles for a moment, but fails to fill with divine energy" if x==0 else ("**EXPLODES** with holy energy, dealing additional damage" if z==1 else "bursts with holy energy, dealing additional damage")}}."   
-f "{{"~~" if x==0 else ""}}Divine Smite Damage{{"~~|~~" if x==0 else "|"}}{{y}}{{"~~" if x==0 else use_slot(%1%)}}"   
-f "Level {{%1%}} Slots |   
{{set("g",get_slots(%1%))}}{{"None" if get_slots_max(%1%) == 0 else ("◉◉◉◉"[:g]+"〇〇〇〇"[g:get_slots_max(%1%)])}}"   
-thumb <image>```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/382205476789551107/unknown.png)