**Wild Magic Surge**  
*By @Croebh, inspired by @Brinjal#4037.*  

I have made my surge command roll for surge, roll the surge, and apply the effects, and works with tides of chaose  
You can roll your surges with: ``!wmsurge`` or ``!wmsurge tides``

```
!alias wmsurge {{g,r,c,R,t=load_json(get_gvar('9274bf9a-f3d2-407e-9723-0a8901d04003')),vroll('1d100'),combat(),vroll('1d20'),1 if '&1&' in 'tides' else 0}}{{g=g[ceil(r.total/2)-1]}}{{'multiline\n!embed' if g.type=='cast' and (R.total==1 or t) else 'embed'}} {{s=[x for x in range(1,10) if get_slots(x)<get_slots_max(x)]}} {{"-desc '*No Wild Surge*'" if R.total>1 and not t else f"-f '{r}{' - Tides of Chaos' if t else ''} | {g.desc}'"}}{{roll=vroll(g.roll) if g.type=='roll' or g.type == 'health' else 0 }}{{mod_hp(roll.total) if g.type=='health' and (R.total==1 or t) else ''}}{{set_slots(s[0],get_slots(s[0])+1) if g.type=='slots' and s and (R.total==1 or t) else ''}}{{set_cc('Sorcery Points', get_cc_max('Sorcery Points')) if g.type == 'cc' and (R.total==1 or t) else ''}}{{c.me.add_effect(g.effect[0],g.effect[2],g.effect[1]) if g.type == 'effect' and c and (R.total==1 or t) else ''}} {{'' if R.total>1 and not t else (f"-f 'Roll|{roll}'" if g.type=='roll' else f"-f 'Health gained|{roll}\n{currentHp}/{hp}'" if g.type=='health' else f"-f 'Regain Slot|{cc_str(s[0]) if s else '*None*'}'" if g.type=='slots' else f"-f 'Sorcerer Points|{cc_str('Sorcery Points')}'" if g.type=='cc' else f"-f 'Gained Effect|Name: {g.effect[0]}\nDuration: {g.effect[1]} rounds'" if g.type =='effect' else '')}} -title "Wild Magic Surge {{'| '+str(R) if not t else ''}}"{{mod_cc('Tides of Chaos',1) if t else ''}} {{f"-f 'Tides of Chaos|Recharged'" if t else ''}}
{{'' if  R.total>1 and not t else (f'!{"i " if c else ""}cast "{g.cast[0]}" -i -l {g.cast[1]} {"-t "+name if g.cast[2] else ""}' if g.type == 'cast' else '')}}
```

And, since it's rather easy to do now that the main part of the code is written, here's a function that lets you search for what a number will result in on the table by doing `!searchsurge <NUMBER>`  


```
!alias searchsurge embed -title "Wild Magic Surge!" -desc "  
{{set("st",(get_gvar("87228cfb-43b6-4cd4-ac2e-14b59db149c0").split("|")))}}{{set("n",ceil(%1%/2))}}{{str(%1%)+": "}}{{st[n-1]}}"

```
