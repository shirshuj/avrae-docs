**As Promised, An all-in-one Paladin Alias, with all Channel Divinities and subclass capstones!**  
*By silverbass#2407*  
  
Counters:  
`!cc create "Divine Sense" -min 0 -max {1+charismaMod} -reset long -type bubble`  
`!cc create "Lay on Hands" -min 0 -max {5*level} -reset long` <--- use PaladinLevel if multiclassing  
`!cc create "Channel Divinity" -min 0 -max 1 -reset short -type bubble`  
`!cc create "Cleansing Touch" -min 0 -max <charismaMod> -reset long -type bubble`  
  
**Subclasses**  
`!cc create "Elder Champion" -min 0 -max 1 -reset long -type bubble`  
`!cc create "Invincible Conquerer" -min 0 -max 1 -reset long -type bubble`  
`!cc create "Exalted Champion" -min 0 -max 1 -reset long -type bubble`  
`!cc create "Holy Nimbus" -min 0 -max 1 -reset long -type bubble`  
`!cc create "Dread Lord" -min 0 -max 1 -reset long -type bubble`  
`!cc create "Avenging Angel" -min 0 -max 1 -reset long -type bubble`  
  
*Next Up: Ranger. I'm gonna start with half-casters and then idk*  
```  
!alias paladin embed   
{{k,r,w,l,a,b="\n###\n","&*&",get_gvar("71c8e803-890a-4944-afb7-c658d6a91aeb").split("\n"),int(PaladinLevel) if exists("PaladinLevel") else level,"&1&".lower(),"&2&".lower()}}{{f,u,g=w[4],w[5],[z.split("|") for z in get_gvar(w[1]).split(k)]}}{{c=[z[0] for z in g if a in z[0].lower()]}}{{c=g[3][0] if a in "cd" else c[0] if c else ""}}{{q=[z.split("|") for z in get_gvar(w[2]).split(k)]}}{{m=[z[0] for z in q if b in z[0].lower()]}}{{m=m[0] if m else ""}}{{x,y=[z[0] for z in g].index(c) if c in [z[0] for z in g] else 0,[z[0] for z in q].index(m) if m in [z[0] for z in q] else 0}}{{h=min(get_cc(c),int(b) if b.isdigit() else 5 if b in g[x][4] else 0) if x==1 and cc_exists(c) else min(9,max(1,int(b if b.isdigit() else 1))) if x==2 else 1}}{{v=get_slots(h)>0 if x==2 else (cc_exists(c) and get_cc(c)>0 and (m if x==3 else 1))}}  
-title "{{name+(" uses " if v else " tries to use ")+("a CRITICAL " if x==2 and "crit" in r else "a ")+g[x][0]+(": "+g[x][3] if x==1 and b in g[x][4] else ": "+str(h) if x==1 else (w[6] if f in r else w[7] if u in r else "") if x==2 else "")+"!" if c else "Paladin"}}"  
-desc "{{get_gvar(w[0]) if not c or (x==3 and not m) else g[x][1]+("\n**DC:** "+str(charismaMod+8+proficiencyBonus) if x==3 else "") if v else g[x][2] if cc_exists(c) or x==2 else w[3]}}"  
{{"-f \""+m+"|"+q[y][1]+"\"" if v and x==3 and m else ""}}  
{{"-f 'Healing|"+(str(h) if x==1 else str(vroll("1d6+"+str(max(1,charismaMod)))) if y==5 else "")+"'" if v and ((x==1 and b.isdigit()) or y==5) else ""}}  
{{"-f 'Damage|"+str(vroll(str((min(h,4)+(2 if f in r or u in r else 1))*(2 if "crit" in r else 1))+"d8"))+"'" if v and x==2 else ""}}  
{{(mod_cc(c,-h) if x!=2 else use_slot(h)) if v else ""}}{{"-f 'Spell Slots|"+slots_str(h)+"'" if x==2 else "-f '"+c+"|"+(cc_str(c) if cc_exists(c) else "*None*")+"'" if c else ""}}  
-color <color> -thumb <image>  
```