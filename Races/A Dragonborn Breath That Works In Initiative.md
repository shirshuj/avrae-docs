**A Dragonborn Breath That Works in Initiative**  
*By silverbass#2407, based off of zhu.exe#4211's `!toll` alias*  
  
**Use with:** `!dborn-breath` or `!dborn-breath TARGET1 TARGET2 ... TARGET9`  
**Requires:** `!cc create "Breath Weapon" -min 0 -max 1 -reset short -type bubble`  
                           `!cvar dborn COLOR` <--- i.e. red, green, blue, silver, etc.  
```  
!alias dborn-breath embed   
{{d,q,r="**Damage:** ","Breath Weapon",get_gvar("597913a2-02db-470a-a233-44f53c75c085").split("\n")}}{{v=cc_exists(q) and get_cc(q)>0 and exists("dborn")}}{{bs,bt="" if not v else "30 ft. line" if dborn.lower() in r[0] else "15 ft. cone","" if not v else "fire" if dborn.lower() in r[1] else "acid" if dborn.lower() in r[2] else "lightning" if dborn.lower() in r[3] else "poison" if dborn.lower() in r[4] else "cold"}}{{a,dc="&1& &2& &3& &4& &5& &6& &7& &8& &9&",constitutionMod+8+proficiencyBonus}}  
{{a,Z,c,g="" if "&1"+"&"=="&1&" else a[:a.find("&")-1].split(" "),vroll(str(floor((level-1)/5)+2)+"d6 ["+bt+"]"),combat() if v else "",get_gvar("234f7f4f-ecb7-4e23-8243-8f92ebe583d5").split("|")}}{{mod_cc(q, -1) if v else ""}}  
-title "<name> {{"uses" if v else "tries to use"}} their {{q}}!" -color <color> -thumb <image>  
{{"-f \"Damage/DC|"+d+str(Z)+"\n**DC:** "+str(dc)+"\"" if v else ""}}  
{{b=[c.get_combatant(n) if n else "" for n in a] if c and a else ""}}{{s=[x.save('con' if dborn.lower() in r[5] else 'dex') for x in b] if b else ""}}{{u=[x.total>=dc for x in s] if s else ""}}{{o=[(("-f \"..."+b[i].name+"|**"+("CON" if dborn.lower() in r[5] else "DEX")+" Save:** "+str(s[i])+"; Failure!\n"+d+str(vroll(str(Z.total)))+"\"") if not u[i] else ("-f \"..."+b[i].name+"|**"+("CON" if dborn.lower() in r[5] else "DEX")+" Save:** "+str(s[i])+"; Success!\n"+d+str(vroll(str(Z.total)+"/2"))+"\""))+("" if (b[i].mod_hp(-Z.total if not u[i] else -Z.total/2)) else "") for i in range(len(b))] if b and v else ""}}  
{{" ".join(o)}}  
{{"-footer \""+" ".join([x.name+": "+x.hp_str() for x in b])+"\"" if b else ""}}  
-f "{{q}}|{{'◉'*get_cc(q) + '〇'*(get_cc_max(q)-get_cc(q)) if cc_exists(q) else "*None*"}}"  
-f "Effect|{{g[0] if not cc_exists(q) else name+g[1]+bs+g[2]+str(dc)+(" Constitution" if dborn.lower() in r[5] else " Dexterity")+g[3]+str(floor((level-1)/5)+2)+"d6 "+bt+g[4] if v else g[5] if not exists("dborn") else g[6]}}"  
```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/452907826344493068/unknown.png)