**Dragon's Breath Spell!**  
*By silverbass#2407*  
  
No requirements, use with `!dbreath-spell [level=2] [TARGET1 TARGET2 ... TARGET99]`  
OR, if you don't use initiative, just use `!dbreath-spell [level=2]`  
  
```  
!alias dbreath-spell embed   
{{lvl,d=2 if "%1"+"%"=="%1%" else int("%1%"),"**Damage:** "}}{{a,dc="&*&",charismaMod+8+proficiencyBonus}}  
{{a,Z,c="" if "&1"+"&"=="&1&" else a.split(" "),vroll(str(1+lvl)+"d6 [acid, cold, fire, lightning, or poison]"),combat()}}  
{{a=a[1:]}}  
-title "<name> uses their Dragon's Breath!" -color <color> -thumb <image>  
{{"-f \"Damage/DC|"+d+str(Z)+"\n**DC:** "+str(dc)+"\""}}  
{{b=[c.get_combatant(n) if n else "" for n in a] if c and a else ""}}{{s=[x.save('dex') for x in b] if b else ""}}{{u=[x.total>=dc for x in s] if s else ""}}{{o=[(("-f \"..."+b[i].name+"|**DEX Save:** "+str(s[i])+"; Failure!\n"+d+str(vroll(str(Z.total)))+"\"") if not u[i] else ("-f \"..."+b[i].name+"|**DEX Save:** "+str(s[i])+"; Success!\n"+d+str(vroll(str(Z.total)+"/2"))+"\""))+("" if (b[i].mod_hp(-Z.total if not u[i] else -Z.total/2)) else "") for i in range(len(b))] if b else ""}}  
{{" ".join(o)}}  
{{"-footer \""+" ".join([x.name+": "+x.hp_str() for x in b])+"\"" if b else ""}}  
-f "Effect|Until the spell ends, you can use an action to exhale energy of the chosen type in a 15-foot cone. Each creature in that area must make a Dexterity saving throw, taking {{1+lvl}}d6 damage of the chosen type on a failed save, or half as much damage on a successful one."  
```