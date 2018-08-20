**Warlock Eldritch Smite**  
*by matthileo#0735 and Croebh#5603*  
  
A snippet for the Eldritch Smite eldritch invocation. Checks for available warlock spell slot, uses it, and display slots remaining.  
`!a staff esmite`  
  
```  
!snippet esmite {{set("slotLevel",min(ceil(WarlockLevel/2),5))}}{{"-phrase \"**Eldritch Smite ("+str(slotLevel)+").** No spell slot available.\"" if get_slots(slotLevel) == 0 else ("-d1 \""+(str(1+slotLevel))+"d8 [eldritch smite, force]\" -phrase \"**Eldritch Smite ("+str(slotLevel)+").** On a hit, the target is knocked prone if it is huge or smaller.\"")+use_slot(slotLevel)}}{{(" -phrase \"__**Remaining Spell Slots**__\" -phrase \"`"+str(slotLevel)+"` "+('◉'*get_slots(slotLevel) + '〇'*(get_slots_max(slotLevel)-get_slots(slotLevel)))+"\"")}}  
```