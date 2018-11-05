# Ammunition, Arrows and Bolts
*By Toothless#7854. Redone by Croebh*

<p align="center">
  <img src="https://i.imgur.com/e06lm9q.png"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/dXi20mT.png"/>
</p>

``ammo`` subtracts 1 from "Ammo" counter and adds 1 to "Used Ammo" counter on attack. ``!collect ammo`` adds half of "Used Ammo" counter to "Ammo", then sets "Used Ammo" to 0. 


``arrow`` subtracts 1 from "Arrows" counter and adds 1 to "Used Arrows" counter on attack. ``!collect arrow`` adds half of "Used Arrows" counter to "Arrows", then sets "Used Arrows" to 0. 


``bolt`` subtracts 1 from "Bolts" counter and adds 1 to "Used Bolts" counter on attack. ``!collect bolt`` adds half of "Used Bolts" counter to "Bolts", then sets "Used Bolts" to 0. 

### Usage

``![attack|a] [atk_name=list] ammo``  
``![attack|a] [atk_name=list] arrow``  
``![attack|a] [atk_name=list] bolt``

``!collect [arrow|bolt|ammo]``

### Setup
Run the snippet or the alias in the **Code** section. It will automatically setup counters. 

**WARNING: Do NOT use -rr, as the snippet will only subtract ONE ammo, not multiple. If you do use -rr, you can manually adjust your counters to fix it.**

``!cc Ammo -[ammo_used]``  
``!cc Arrows -[arrows_used]``  
``!cc Bolts -[bolts_used]``

``!cc "Ammo Used" +[ammo_used]``  
``!cc "Arrows Used" +[arrows_used]``  
``!cc "Bolts Used" +[bolts_used]``

### Code
```GN
!snippet arrow {{c='Arrows'}}
{{v,C=cc_exists(c),'Used '+c}}
{{create_cc_nx(c, 0)}}
{{create_cc_nx(C, 0)}}
{{"" if v else set_cc(c, 20)}}
{{v=1 if get_cc(c) > 0 else 0}}
{{mod_cc(c, -1) if v else ""}}
{{mod_cc(C, 1) if v else ""}}
{{"" if v else "miss"}}
{{"" if v else '-f "Ammunition|You can use a weapon that has the ammunition property to make a ranged attack only if you have ammunition to fire from the weapon. (PHB 146)"'}}
-f "{{c}} ⏐ {{C}} | {{get_cc(c)}} ⏐ {{get_cc(C)}}"
```

```GN
!snippet bolt {{c='Bolts'}}
{{v,C=cc_exists(c),'Used '+c}}
{{create_cc_nx(c, 0)}}
{{create_cc_nx(C, 0)}}
{{"" if v else set_cc(c, 20)}}
{{v=1 if get_cc(c) > 0 else 0}}
{{mod_cc(c, -1) if v else ""}}
{{mod_cc(C, 1) if v else ""}}
{{"" if v else "miss"}}
{{"" if v else '-f "Ammunition|You can use a weapon that has the ammunition property to make a ranged attack only if you have ammunition to fire from the weapon. (PHB 146)"'}}
-f "{{c}} ⏐ {{C}} | {{get_cc(c)}} ⏐ {{get_cc(C)}}"
```

```GN
!snippet ammo {{c='Ammo'}}
{{v,C=cc_exists(c),'Used '+c}}
{{create_cc_nx(c, 0)}}
{{create_cc_nx(C, 0)}}
{{"" if v else set_cc(c, 20)}}
{{v=1 if get_cc(c) > 0 else 0}}
{{mod_cc(c, -1) if v else ""}}
{{mod_cc(C, 1) if v else ""}}
{{"" if v else "miss"}}
{{"" if v else '-f "Ammunition|You can use a weapon that has the ammunition property to make a ranged attack only if you have ammunition to fire from the weapon. (PHB 146)"'}}
-f "{{c}} ⏐ {{C}} | {{get_cc(c)}} ⏐ {{get_cc(C)}}"
```

```GN
!alias collect embed
{{c='Arrows' if '&' in '&1&' else 'Bolts' if '&1&'.lower() in 'bolts' else 'Arrow' if '&1&'.lower() in 'arrows' else 'Ammo'}}
{{v,C=cc_exists(c),'Used '+c}}
{{create_cc_nx(c, 0)}}
{{create_cc_nx(C, 0)}}
{{"" if v else set_cc(c, 20)}}
{{u=max(0,get_cc(C))}}
{{r=vroll(f"{get_cc(c)}+({u}/2)")}}
{{v=u!=0}}
{{set_cc(c, r.total)}}
{{set_cc(C, 0)}}
-title "<name> {{"collects" if v else "attempted to collect"}} their ammunition!"
-desc "{{"At the end of the battle, you can recover half your expended ammunition by taking a minute to search the battlefield." if v else "You do not have any expended ammunition to recover."}}"

{{"-f \"" + C + " | " + str(u) + "\"" if v else ""}}
{{"-f \"" + c + " | " + str(r) + "\"" if v else ""}}
-footer "Weapons | PHB 146"
-color <color>
-thumb <image>
```
