**Paladin Channel Divinity **  
*By Croebh#5603*  
  
An alias to use the Channel Divinity Paladin class feature. This one is set up for the Oath of Vengeance archetype, shouldn't be hard to change the wording around to match other oaths. Please set up the Cvar and CC as per the first two commands.   
  
`!divinity [abjure|enmity]`  
  
If you mispell the argument, it will remind you of the proper one. If you have no remaining charges (courtesy of the custom counter) it will fizzle on you, reminding you to rest before trying again.  
  
`!cvar spellsave {8+proficiencyBonus+charismaMod} `  
  
`!cc create "Channel Divinity" -reset short -max 1 -min 0 -type bubble`  
```!alias divinity embed   
-title "<name> Channels Divinity: {{"FIZZLE" if get_cc("Channel Divinity")==0 else "Vow of Enmity" if str("%1%")=="enmity" else "Abjure Enemy" if str("%1%")=="abjure" else "Uuuuh"}}"  
-desc "{{"The channel fails, as they need to have a short or long rest before channeling again." if get_cc("Channel Divinity")==0 else str("As an action, you present your holy symbol and speak a prayer of denunciation, using your Channel Divinity. Choose one creature within 60 feet of you that you can see. That creature must make a Wisdom saving throw \(**"+spellsave+"**\), unless it is immune to being frightened. Fiends and undead have disadvantage on this saving throw.\n\nOn a failed save, the creature is frightened for 1 minute or until it takes any damage. While frightened, the creature's speed is 0, and it can't benefit from any bonus to its speed.\n\nOn a successful save, the creature's speed is halved for 1 minute or until the creature takes any damage.") if str("%1%")=="abjure" else str("As a bonus action, you can utter a vow of enmity against a creature you can see within 10 feet of you, using your Channel Divinity. You gain advantage on attack rolls against the creature for 1 minute or until it drops to 0 hit points or falls unconscious.") if str("%1%")=="enmity" else str("You didnt specify a type, dummy.\n\n`!divinity abjure` for **Abjure Enemy**, or \n`!divinity enmity` for **Vow of Enmity**.")}}"{{mod_cc("Channel Divinity", -1) if str("%1%")=="enmity" or str("%1%")=="abjure" else ""}}```