**XGtE Encounter Roller I guess?**  
*By silverbass#2407, suggestion by I'm Cave Johnson...#8397*  
  
**Use With:** `!enc [terrain] [level]`  
```  
!alias enc embed  
{{j=load_json(get_gvar("3698b043-b51c-45cd-8ece-fb25030070dd"))}}  
{{c="arctic" if "&1"+"&"=="&1&" else "&1&".lower()}}  
{{l=int("&2&") if "&2&".isdigit() else 1}}  
{{t=3 if l>=17 else 2 if l>=11 else 1 if l>=5 else 0}}  
{{b="" if "list" in "&*&" or "&1"+"&"=="&1&" else [e for e in j['encounter'] if c in e.location.lower()]}}  
{{b=b[0] if b else ""}}  
{{r=vroll("1d100")}}  
-title "{{"Terrain-Based" if not b else b.location }} Encounter{{"" if not b else " (Levels "+str(b.tables[t].minlvl)+"-"+str(b.tables[t].maxlvl)+")"}}"  
-desc "{{"\n".join([e.location for e in j['encounter']]) if not b  else str(r)+"\n"+"".join([(x.enc[:x.enc.index("|")] if "|" in x.enc else x.enc).replace("{@creature","").replace("{@italic","").replace("}","").replace("  "," ").replace("( ","(")+(")" if "|" in x.enc and ")" in x.enc[x.enc.index("|"):] else "")+(": "+str(vroll(x.enc)) if x.enc[0].isdigit() else "") for x in b.tables[t].table if int(x.min)<=r.total<=int(x.max)])}}"  
-footer "Use With: !enc [terrain] [level], !enc list"  
-color <color>  
```