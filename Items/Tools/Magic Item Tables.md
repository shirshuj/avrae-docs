**Magic Item Tables**  
  
The `!hoard` alias automatically rolls on the magic item table, but you can use this alias if you want to roll on this table without the rest of the hoard!  
  
Use with: `!mitable [table letter a-i] [number of rolls, can be dice]`  
  
```  
!alias mitable embed {{t,r,g='&1&'.upper() if '&' not in '&1&' and '&1&'.upper() in list('ABCDEFGHI') else 'A',vroll('&2&' if '&2&'!='&2'+'&' else '1'),load_json(get_gvar('2c232804-aac9-4195-a5d9-d35f7315f6c4'))}} -footer "{{g['footer']}}" {{g=g['magicItems'][t]}}
-title "{{f"Rolling for {r.total} Item{'s' if r.total>1 else ''} on Magic Item Table {t}"}}"
-desc "{{"**Number of Rolls: ** "+str(r)+"\n" if r.total>1 else ""}}{{"\n".join([("" if set("v",vroll("1d100")) else "")+f'1d100 = `{str(v.total):0>2}` - '+"".join([m.name if m.min<=v.total<m.max else "" for m in g]) for i in range(1,r.total+1)])}}"
```
