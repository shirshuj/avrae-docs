**Fighter's Action Surge, Second Wind, and Indomitable, AND ALL THE OTHER SUBCLASS FEATURES, now in one alias!**  
*By silverbass#2407*  
  
**Requires:** custom counters  
`!cc create "Action Surge" -type bubble -reset short -min 0 -max 1` (use 2 if over level 18)  
`!cc create "Second Wind" -type bubble -reset short -min 0 -max 1`  
`!cc create "Indomitable" -type bubble -reset long -min 0 -max 1` (use 2 or 3 if over levels 13 and 17)  
  
`!cc create "Superiority Dice" -type bubble -reset short -min 0 -max 4` for battle master, change dice number as needed  
`!cc create "Arcane Shot" -type bubble -reset short -min 0 -max 2` for arcane archer  
`!cc create "Warding Maneuver" -type bubble -reset long -min 0 -max <constitutionMod>` for cavalier  
`!cc create "Unwavering Mark" -type bubble -reset long -min 0 -max <strengthMod>` for cavalier  
`!cc create "Fighting Spirit" -type bubble -reset long -min 0 -max 3` for samural  
`!cc create "Strength Before Death" -type bubble -reset long -min 0 -max 1` for samurai  
  
*Next up: Paladin...probably... smite is annoying and channel divinity has a bazillion options*  
```!alias fighter embed   
{{p,w,l,a,b=proficiencyBonus,get_gvar("990dc1ad-ae0f-46b3-8126-8b562725c421").split("\n"),int(FighterLevel) if exists("FighterLevel") else level,"&1&".lower(),"&2&".lower()}}{{g,d=[z.split("|") for z in get_gvar(w[1]).split("\n###\n")],d if exists("d") else "d8" if l<10 else "d10" if l<18 else "d12"}}{{c=[z[0] for z in g if a in z[0].lower()]}}{{c=g[0][0] if a in "2nd" else g[3][0] if a=="bm" else c[0] if c else ""}}{{q=[z.split("|") for z in get_gvar(w[3 if "Arc" in c else 2]).split("\n###\n")]}}{{m=[z[0] for z in q if b in z[0].lower()]}}{{m=m[0] if m else ""}}{{x,y=[z[0] for z in g].index(c) if c in [z[0] for z in g] else 0,[z[0] for z in q].index(m) if m in [z[0] for z in q] else 0}}{{c=g[3][3] if x==3 else c}}{{v=cc_exists(c) and get_cc(c)>0 and (m if 5>x>2 else 1)}}  
-title "{{name+(" uses " if v else " tries to use ")+g[x][0]+"!" if c else "Fighter"}}"  
-desc "{{get_gvar(w[0]) if not c or (5>x>2 and not m) else g[x][1]+("\n**DC:** "+str(max(dexterityMod,strengthMod)+8+p) if x==3 else "\n**DC:** "+str(intelligenceMod+8+p) if x==4 else "") if v else g[x][2] if cc_exists(c) else w[4]}}"  
{{h=vroll("1d10+"+str(l))}}{{"-f \"Healing|"+str(h)+"\" -f \"Hit Points|"+("" if set_hp(min(hp,h.total+get_hp())) else "")+str(get_hp())+" / "+str(hp)+"\"" if v and x==0 else ""}}  
{{"-f \"AC Increase|"+str(vroll("1d8"))+"\"" if x==6 else ""}}  
{{set_temphp(5) if x==7 and v else ""}}  
{{"-f \""+m+"|"+q[y][1].replace("%D%",(str(vroll(q[y][(2 if l<18 else 3)])) if x==4 else ""))+"\"" if v and 5>x>2 and m else ""}}  
{{("-f \"Bonus to Hit|"+str(vroll(d))+"\"" if "Pr" in m else "-f \"New AC|"+str(vroll(d+"+"+str(armor)))+"\"" if "Ev" in m else "-f \"Reduced By|"+str(vroll(d+"+"+str(dexterityMod)))+"\"" if "Pa" in m else "-f \"Damage|"+str(vroll(d))+"\"") if v and x==3 and m else ""}}  
{{mod_cc(c,-1) if v else ""}}{{"-f \""+c+"|"+(cc_str(c) if cc_exists(c) else "*None*")+"\"" if c else ""}}  
-color <color> -thumb <image>  
```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/464606212504420353/Screenshot_20180705-193834_Discord.jpg)