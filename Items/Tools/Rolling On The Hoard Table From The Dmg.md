**Rolling on the Hoard Table from the DMG**  
*By Croebh#5603 and silverbass#2407*  
  
Use with `!hoard [cr]` (force a result with `!hoard [cr] [roll]`  
  
```  
!servalias hoard embed {{cr,ttl=int("&1&") if "&1&".isdigit() else 1,0}}  
{{p=get_gvar('b7e6ad10-f474-4869-be7f-66237b6862fd').split("\n")}}{{r,n,e=vroll("&2&" if "&2"+"&"!="&2&" and "&2&".isdigit() else '1d100'),get_gvar(p[4]).split("\n"),get_gvar(p[5]).split('|')}}  
{{b=0 if cr<5 else 1 if cr<11 else 2 if cr<17 else 3}}  
{{h='ABCDEFGHI'}}  
{{g=get_gvar('b04f792c-7644-451c-bedd-9c536d8150c4').split('\n###\n')}}  
{{g=[x.split('\n') for x in g]}}  
{{c=[y for y in [d.split(',') for d in get_gvar(p[b]).split("\n")] if r.total in range(int(y[0]),int(y[1]))]}}{{c=c[0]}}  
-title "Hoard Table for CR {{cr}} ({{'0-4' if b==0 else '5-10' if b==1 else '11-16' if b==2 else '17+'}})"  
-desc "{{r.dice}}"  
-f "Currency|{{"".join([("" if set("u",vroll(k[:-2])) else "")+("" if set("ttl",ttl+(u.total*(10 if k[-2:]=="PP" else 0.5 if k[-2:]=="EP" else 0.1 if k[-2:]=="SP" else 0.01 if k[-2:]=="CP" else 1))) else "")+str(u)[:-1]+" "+k[-2:]+"`\n" if k!='0' else "" for k in n[b].split(',')])+"\n**Total Value:** "+f"{round(float(ttl),2):,}"+" GP"}}"  
{{rr=[vroll(c[x]) for x in range(2,len(c))]}}  
{{[str(r) for r in rr]}}  
{{" ".join([("-f \""+e[i+2]+"|"+str(rr[i])+"\"" if rr[i].total>0 else "") for i in range(11)])}}  
-footer "{{p[6]}}"  
{{" ".join([(("" if set("lines",[line.split("|") for line in g[i]]) else "")+"-f \""+str(e[13+i])+"|**Number of Rolls:** "+str(rr[11+i])+"\n"+"\n".join([("" if set("r",vroll("1d100")) else "")+str(r)+" - "+"".join([line[2] if int(line[0])<=r.total<int(line[1]) else "" for line in lines]) for j in range(1,rr[11+i].total+1)])+"\"" if rr[11+i].total>0 else "") for i in range(0,len(h))])}}  
```  
  
Still adding features so stay tuned for updates!