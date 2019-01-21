# setrace
*By Derixyleth#0636.*

Sets your race, sets up any custom counters for that race, adds cvars for languages, resistances, size, speeds, and senses. Supports all published races, the races from Wayfinder's Guide to Eberron, and some others. Can also make racial aliases, though not all are covered yet. Run it without any arguments to set your race based on the one in your sheet.

`!setrace` to set your race, and create counters
`!setrace make` to do the above, and try to make an alias, if any, for using ratial abilities

```md
!alias setrace {{G,g,v=get_raw(),load_json(get_gvar("c6f5cae2-3275-4726-abb7-7a6880b036e6")),2.3}}{{S=[set(x,g.v[x])for x in g.v]}}{{a="&*&" if "&*&" and not m=="&*&"[:4] else G.race+(" "+m if m in "&*&" else "") if "race" in G else B}}{{S=[set("a",a.replace(x,g.Q[x]))for x in g.Q]}}{{a=a.lower().split()}}{{M,H,V,P=m in a,h in a or not a,R.v,u in a}}{{r=B if H else a[:(a.index(m)if M else len(a))]}}{{i=H or P}}{{Z,n=[x for x in g.r if all([(y in x.r) for y in r])]if a else B,a.index(m)+1 if M else 0}}{{S=(R.update(Z[0]),V.update(Z[0].v))if Z else""}}{{N,AN=B if i else V.race if R.r else(" ".join(r)).title(),a[n]if n and len(a)>n else V.race.lower().replace(" ","-")}}{{S=B if i or R.r else V.update({"race":N})}}{{S=B if i else([set_cvar(x,V[x])for x in V if (x in G and not G[x])or not x in G],[delete_cvar(x)for x in D if not x in V],[create_cc_nx(R.cc[x],0,proficiencyBonus if V.race=="Blink Dog" else 1,R.cr[x],b)if level>=R.cl[x]else B for x in R.cn])}}{{c=[R.cc[x] for x in R.cn if level>=R.cl[x]]if Z else B}}{{I=[x.v.race for x in g.r if"AL"in x and x.AL[:2]=="9c"]}}{{I.sort()}}{{((U*(M or P)+et+(g.U if P else name+(nh if H else sr if Z else un)+(Q+g.H if H else (f+f.join([g.f[x]+V[x]for x in V if(x!="dborn"if[(y in"wolf")for y in r]else 1)])+(f+cc+o.join(c) if c else B)+(f+af+"**"+R.f+":** "+R.fd if M and"fd"in R else B)+Q)+(B if R.r else g.u)))+g.F+color+g.t+image).replace("VER",str(v)+(nu if v<g.V else B)).replace("RN",N)+'\n'+((get_gvar(R.AL).replace("AN",AN).replace("IN",o.join(I))if"AL"in R else g.NO.replace("NA",name)).replace("RN",N)if M else "!"+"serv"*("&2&"in"server")+get_gvar(g.up) if P else B))}}
```
