**Cleric Channel Divinity**  
*By Croebh#5603*  
An alias to use the Channel Divinity Cleric class feature. This one is set up for the Grave domain, shouldn't be hard to change the wording around to match other domains. Please set up the Cvar and CC as per the first two commands.   
  
!divinity [path|turn]  
  
If you mispell the argument, it will remind you of the proper one. If you have no remaining charges (courtesy of the custom counter) it will fizzle on you, reminding you to rest before trying again.  
  
`!cvar spellsave {8+proficiencyBonus+wisdomMod}`  
  
`!cc create "Channel Divinity" -reset short -max {{3 if level > 17 else 2 if level > 5 else 1}} -min 0 -type bubble`  
```py  
!alias divinity embed {{set("x", "Channel Divinity")}}  
-title "<name> Channels Divinity: {{"FIZZLE" if get_cc(x)==0 else "Path of the Grave" if str("%1%")=="path" else "Turn Undead" if str("%1%")=="turn" else "Uuuuh"}}"  
-desc "{{"The channel fails, as they need to have a short or long rest before channeling again." if get_cc("Channel Divinity")==0 else str("As an action, you choose one creature you can see within 30 feet of you, cursing it until the end of your next turn. The next time you or an ally of yours hits the cursed creature with an attack, the creature has vulnerability to all of that attack's damage, and then the curse ends.") if str("%1%")=="path" else str("As an action, you present your holy symbol and speak a prayer censuring the undead. Each undead that can see or hear you within 30 feet of you must make a **DC"+spellsave+"** Wisdom saving throw. If the creature fails its saving throw, it is turned for 1 minute or until it takes any damage.\n\nA turned creature must spend its turns trying to move as far away from you as it can, and it can't willingly move to a space within 30 feet of you. It also can't take reactions. For its action, it can use only the Dash action or try to escape from an effect that prevents it from moving. If there's nowhere to move, the creature can use the Dodge action.") if str("%1%")=="turn" else str("You didnt specify a type, dummy.\n\n`!divinity path` for **Path of the Grave**, or \n`!divinity turn` for **Turn Undead**.")}}"{{mod_cc(x, -1) if str("%1%")=="turn" or str("%1%")=="path" else ""}}   
-f "Channel Divinities | {{get_cc(x)}}/{{get_cc_max(x)}}"```