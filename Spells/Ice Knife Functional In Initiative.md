**Ice Knife, functional in initiative**  
*By silverbass#2407 stealing ChaoticUnreal#4387's framework*  
  
**Use With:** `!iceknife target1 target2 ... target99` OR `!iceknife slot_level target1 target2 ... target99`. Target1 is the one hit by the initial 1d10 attack.  
Can also just be used with just `!iceknife` or `!iceknife slot-level` with no targets for those who don't use initiative.  
```  
!alias iceknife embed   
{{a="&*&"}}{{c,z,y,x,w=combat()," adv" in a and not " dis" in a," dis" in a and not " adv" in a," ea" in a and not " dis" in a," crit" in a}}{{sl,i=max(min(9,int("&1&")),1) if "&1&".isdigit() else 1,"-i" in a}}{{v,ab=get_slots(sl)>0 or i,max(intelligenceMod,wisdomMod,charismaMod)+proficiencyBonus}}{{a=a.replace(" adv","").replace(" dis","").replace(" ea","").replace(" crit","").replace(" -i","").split(" ")}}  
{{a=a[1:] if "&1&".isdigit() else a}}{{ar=vroll(("2d20kh1+" if z else "2d20kl1+" if y else "3d20kh1+" if x else "1d20+")+str(ab))}}  
{{w=ar.total==20+ab or w}}  
{{dr1,dr2=vroll(("2" if w else "1")+"d10 [piercing^]"),vroll(str(1+sl)+"d6 [cold]")}}  
{{use_slot(sl) if v and not i else ""}}{{ot=c.get_combatant(a[0]) if c and len(a) else ""}}  
-title "<name> {{"casts" if v else "attempts to cast"}} Ice Knife{{" at "+ot.name if ot else ""}}!"  
{{"-f \"Attack|**To Hit:** "+str(ar)+("\n**Damage"+(" (CRIT)" if w else "")+":** "+str(dr1) if not ot or ot.wouldhit(ar.total) else "\n**Miss**")+"\"" if v else ""}}  
{{"-f 'Damage/DC|**Damage:** "+str(dr2)+"\n**DC:** "+str(ab+8)+"'" if v else ""}}  
{{ot.mod_hp(-dr1.total if ot.wouldhit(ar.total) else 0) if ot else ""}}{{b=[c.get_combatant(n) if n else "" for n in a] if c and a else ""}}{{s=[j.save("dex") if j else "" for j in b] if b else ""}}{{u=[j.total>=8+ab if j else "" for j in s] if s else ""}}  
{{o=[("-f '..."+b[i].name+"|**DEX Save:** "+str(s[i])+("; Failure!\n**Damage:** "+str(vroll(str(dr2.total)))+"'" if not u[i] else "; Success!\n**Damage:** "+str(vroll(str(dr2.total)+"/2"))+"'")+("" if (b[i].mod_hp(-dr2.total if not u[i] else -dr2.total/2)) else "")) if b[i] else "" for i in range(len(b))] if b and v else ""}}  
{{" ".join(o)}}  
-f "Spell Slots|`{{sl}}` {{('◉'*(get_slots(sl))+'〇'*(get_slots_max(sl)-(get_slots(sl)))) if get_slots_max(sl)>0 else ""}}"  
-thumb <image> -color <color>  
{{"-footer '"+" ".join([j.name+": "+j.hp_str() if j else "" for j in b])+"'" if b else ""}}  
```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/458499537653465098/unknown.png)