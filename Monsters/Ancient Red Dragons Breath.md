**Ancient Red Dragon's Breath**  
*By silverbass#2407*  
  
This uses a homebrew ancient red dragon's alternate breath attack too, which is pretty neat. I've attached the PDF for those interested.  
This breath feature works both in and out of initiative, and will automatically apply damage to targets and roll saves. BE WARY THOUGH, IT DOES NOT TAKE INTO ACCOUNT RESISTANCES/VULNERABILITIES/IMMUNITIES.  
   
Use With: `!VRE-breath TARGET1 TARGET2 ... TARGET9`, or for the alternate breath, use `!VRE-breath intense TARGET1 TARGET2 ... TARGET9`  
  
For those seeking to do other dragons, @ me and I can help with converting it for the other colors  
```  
!alias VRE-breath embed   
{{d,q,bt,a="**Damage:** ","Breath Weapon","Intense Heat" if "int" in "&1&".lower() else "Fire Breath","&1& &2& &3& &4& &5& &6& &7& &8& &9& &10&"}}{{v=cc_exists(q) and get_cc(q)>0}}  
{{a,Z,c,g="" if "&1"+"&"=="&1&" else a[:a.find("&")-1].split(" "),vroll("13d6 [fire]" if bt=="Intense Heat" else "26d6 [fire]"),combat() if v else "",get_gvar("a8ba5d1a-7bb6-479c-b112-56c2ba04949d").split("|")}}{{a=a[1:] if a and a[0].lower() in "intense heat fire breath" else a}}  
{{mod_cc(q, -1) if v else ""}}  
-title "<name> {{"uses" if v else "tries to use"}} their {{bt}}!" -color <color> -thumb <image>  
{{"-f \"Damage/DC|"+d+str(Z)+"\n**DC:** 24\"" if v else ""}}  
{{b=[c.get_combatant(n) if n else "" for n in a] if c and a else ""}}{{s=[x.save('dex') for x in b] if b else ""}}{{u=[x.total>=24 for x in s] if s else ""}}{{o=[(("-f \"..."+b[i].name+"|**DEX Save:** "+str(s[i])+"; Failure!\n"+d+str(vroll(str(Z.total)))+"\"") if not u[i] else ("-f \"..."+b[i].name+"|**DEX Save:** "+str(s[i])+"; Success!\n"+d+str(vroll(str(Z.total)+"/2"))+"\""))+("" if (b[i].mod_hp(-Z.total if not u[i] else -Z.total/2)) else "") for i in range(len(b))] if b and v else ""}}  
{{" ".join(o)}}  
{{"-footer \""+" ".join([x.name+": "+x.hp_str() for x in b])+"\"" if b else ""}}  
-f "{{q}}|{{'◉'*get_cc(q) + '〇'*(get_cc_max(q)-get_cc(q)) if cc_exists(q) else "*None*"}}"  
-f "Effect|{{g[0] if not cc_exists(q) else name+g[1] if not v else name+g[3] if bt=="Intense Heat" else name+g[2]}}"  
```