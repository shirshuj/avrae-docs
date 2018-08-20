**Also, Magic Item Tables**  
  
The `!hoard` alias automatically rolls on the magic item table, but you can use this alias if you want to roll on this table without the rest of the hoard!  
  
Use with: `!mitable [table letter a-i] [number of rolls, can be dice]`  
  
```  
!servalias mitable embed {{t,h='&1&'.upper(),'ABCDEFGHI'}}{{g,n,b=get_gvar('b04f792c-7644-451c-bedd-9c536d8150c4').split('\n###\n'),vroll('&2&' if '&2&'!='&2'+'&' else '1'),h.index(t) if t in h and t!='&1'+'&' and t.isalpha() else 0}}  
{{g=[x.split('\n') for x in g]}}  
{{lines=[line.split("|") for line in g[b]]}}  
-title "Rolling for {{str(n.total)+(" Items" if n.total>1 else " Item")}} on Magic Item Table {{h[b]}}"  
-desc "{{"**Number of Rolls: ** "+str(n)+"\n" if n.total>1 else ""}}{{"\n".join([("" if set("r",vroll("1d100")) else "")+str(r)+" - "+"".join([line[2] if int(line[0])<=r.total<int(line[1]) else "" for line in lines]) for i in range(1,n.total+1)])}}"  
```