# Armor of Agathys
*By Derix*

`!aga cast [slot level]` will cast armor of Agathys and set you up with the proper temp HP.
`!aga <attacker>` will deal the cold damage to your attacker.
`!aga drop` will remove the temp HP.

### Code
```GN
!alias aga {{c,slvl,h=combat(),int("&2&") if "&2&".isdigit() else min(5,ceil(int(WarlockLevel)/2) if exists("WarlockLevel") else ceil(level/2) if get_slots(ceil(level/2)) else 1),not "&*&" or "&1&" in "help"}}{{sc,dr="&1&" in "cast" and get_slots(slvl),"&1&" in "drop"}}{{t=c.get_combatant("&*&") if not sc and c and "&*&" else None}}{{set_cvar("aglvl",slvl) if sc else delete_cvar("aglvl") if dr else ""}}{{ena,na,idmg=t.name if t else "&*&".title(),name,5*int(aglvl)if exists("aglvl") else 0}}{{set_temphp(idmg) if sc else set_temphp(0) if dr else ""}}{{delete_cvar("aglvl")if t and not get_temphp() else ""}}{{'embed -title "How to use !aga" -f "Casting|`!aga cast [slot level]` will cast *armor of Agathys* and set you up with the proper temp HP." -f "Getting Hit|`!aga <attacker>` will deal the cold damage to your attacker." -f "Dropping the Spell|`!aga drop` will remove the temp HP."' if h else 'cast agathys -l '+str(slvl)+' -f "Temp HP|'+str(get_temphp())+'"' if sc else 'embed -title "'+ena+' is struck by shards of ice!" -desc "If a creature hits you with a melee attack while you have temporary hit points from the *armor of Agathys* spell, the creature takes '+str(idmg)+' cold damage." -f "'+ena+'|'+t.damage(str(idmg)+'[cold]').damage+'" -footer "'+ena+': '+t.hp_str()+'"'+' -f "Remaining Temp HP|'+str(get_temphp())+'"' if t else ('embed -title "'+name+('\'s Armor of Agathys fades!" -f "Temp HP|0" -f "Outgoing Cold Damage|0"' if "&1&" in "drop" else ' tries to cast Armor of Agathys" -desc "But has no remaining '+str(slvl)+('st' if slvl<2 else 'nd' if slvl<3 else 'rd' if slvl<4 else 'th')+' level spell slots." -f "Spell Slots|'+slots_str(slvl)+'"' if "&1&" in "cast" else ' did something wrong." -desc "You entered an incorrect subcommand or tried to pass an invalid target."'))+' -footer "For help using !aga, run !aga help"'}}
```
