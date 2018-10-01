# Concentration Manager
*By Derixyleth#0636.*

Casts concentration spells and manages concentration with a cvar and notes and built-in DC calculator.

### Setup
No setup required, run `!conc` with no arguments for a full rundown of how to use it.

### Code
```
!alias conc {{n,dmg,args,c,cn,ds,os,H,W,C=name,int("&1&") if "&1&".isdigit() else 0,"&*&".replace("&1& ",""),combat(),str(get_gvar("c36b0308-9436-4ea8-bf58-affce95e14cb")).split("~"),"&1&" in "drop" or "&1&" in "dorp",concSpell if exists("concSpell") else "",len("&*&")<1 or "&1&" in "help","&1&"=="?","&1&"=="cast"}}{{SN=str("&2&").lower()}}{{nN=dmg or H or W}}{{k=-1}}{{IDK=[set("k",x if SN in get_raw().spellbook.spells[x].lower() else k) for x in range(len(get_raw().spellbook.spells))] if C else ''}}{{"" if nN else set_cvar("concSpell","" if ds else (get_raw().spellbook.spells[k] if k+1 else "&2&") if "cast"=="&1&" else"&*&")}}{{"" if nN or not c else c.me.set_note(c.me.note.replace("**Concentrating** on the *"+os+"* spell.\n","")) if ds else c.me.set_note("**Concentrating** on the *"+concSpell+"* spell.\n"+(str(c.me.note) if c.me.note else ""))}}{{nC=concSpell==""}}{{'multiline\n!'+('i ' if '-t' in args and c else '')+'&*&'+'\n!' if C else ''}}{{cn[0]+cn[1]+'"'+cn[2] if H else 's con '+args+' -dc '+str(max(floor(dmg/2),10))+' -title "'+n+' makes a Concentration Check!" -f "Losing Concentration|'+cn[1]+'"' if dmg else 'embed -title "'+n+(' stops concentrating'+(', despite spelling "drop" wrong!' if "&1&"=="dorp" else '')+'!" -desc "'+n+' is no longer concentrating on the *'+os+'* spell.' if ds and os else (' is'+(' not' if nC else '') if W or ds else ' begins')+' concentrating!" -desc "'+n+' is '+('not' if nC else 'currently' if W else 'now')+' concentrating on '+('any' if nC else 'the *'+concSpell+'*')+' spell.'+('' if nC else ' If you lose concentration, the spell ends." -f "Losing Concentration|'+cn[1]))+'"'}}{{cn[3]}} -color <color> -thumb <image>
```
