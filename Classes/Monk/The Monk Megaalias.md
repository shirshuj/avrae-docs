**The Monk Megaalias**  
*By silverbass#2407*  
  
I know i promised to do ranger next, but I ended up with monk instead. If you play 4 elements or sun soul, just know i've ignored you. I may get to it later, but at least not for now.  
  
Setup: nadizak#5061's !level alias does most of it for gsheet and ddb; for DiceCloud, just set it up properly and use !update -cc  
```  
!alias monk embed -color <color> -thumb <image> {{w,g,a,l,B=wisdomMod,load_json(get_gvar("6687a6d3-92fe-4ce9-86c6-fbe26f9e5970")),"&1&",int(MonkLevel)if exists("MonkLevel")else level,""}}{{x=[x for x in g if'name'in x and a.lower()in x.name.lower()]if a else B}}{{x=x[0]if x else B}}{{n=x.name if'name'in x else B}}{{m=int("&2&")if"&2&".isdigit()and x and("Slo"in n or"efl"in n)else 0}}{{s=int("&2&")if"&2&".isdigit()and not m else 0}}{{q=(x.num if'num'in x else 1)+s}}{{d=0 if not n else vroll(f"{2*s}d10")if"Long"in n else vroll("10d10")if"Qui"in n else l*5 if"Slo"in n else vroll(f"1d10+{dexterityMod+l}")if"Defl"in n else l+w if"of D"in n else 0}}{{cc="Ki"if'cc'in x and x.cc=="Ki Points"and cc_exists("Ki")else x.cc if'cc'in x else B}}{{v=('y'in x and cc_exists(cc)and get_cc(cc)>=q)if cc else 1}}{{q=0 if'name'in x and"Mas"in n and get_hp()>0 else q}}
-title "{{f"{name} {'uses'if v else'tries to use'} {n}"if x else"Monk"}}"
-desc "{{get_gvar(g[1])if not x else g[0]if(cc and not cc_exists(cc))else (x.y.replace("#d#",str(d))if d else x.y)+((f"\n\n{x.drunk}"+(f"\n\n{x.drunk17}"if l>=17 else B))if"Flu"in n and exists("subclass")and"unk"in subclass else B)+(f"\n\n{x.open}"if"Flu"in n and exists("subclass")and"Op"in subclass else B) if v else x.n}}"
{{mod_cc(cc,-q)if cc and v and (get_cc(cc)==0 if"erf"in n else 1) else B}}
{{f"-f '{cc}|{cc_str(cc)}'"if cc and cc_exists(cc) else B}}    
{{r=min(m,(d if str(d).isdigit()else d.total))}}{{f"-f 'Reduced by|{r}' -f 'Hit Points|{B if set_hp(min(hp,r+get_hp()))else B}{get_hp()} / {hp}'"if v and d and m else B}}
{{"-f 'Hit Points|{B set_hp(1 if'Mas'in n and get_hp()<=0 else min(hp,get_hp()+3*l)if'Who'in n else get_hp())else B}{get_hp()} / {hp}'"if v and'name'in x and("Mas"in n or "Who" in n)else B}}
{{(B if set_temphp(l+w) else B)+f"-f 'Temp HP|{l+w}'"if'name'in x and"of D"in n and v else B}}
{{"-f 'Damage|"+str(vroll("1d"+str(int((l+13)/6)*2)))+"'"if'name'in x and'eft'in n and v else B}}
```
