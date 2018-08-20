**The Sorcerer - Empowered Spell**  
*By Toothless#7854*  
  
A way to reroll dice using Empowered Spell. Usage is ``!empower <diceToReroll> <oldTotal>`` such as ``!empower 3d6 3``. Automatically subtracts a sorcery point, displays the old dice and total, rerolls the dice, and displays the difference.  
  
To set your color, type ``!cvar color <hex>``, replacing ``<hex>`` with a hex code. **WARNING:** Currently does not limit the dice rerolled to your Charisma modifier.   
  
This alias will eventually be moved to **Advanced Avrae - The Sorcerer** when it is completed.  
  
```!alias empower embed {{set("counter", "Sorcery Points")}} {{mod_cc(counter, -1, True)}} {{set("oldDice", "%1%")}} {{set("oldTotal", "%2%")}} {{set("rerollDice", vroll(oldDice))}} {{set("sign", "+" if rerollDice.total >= int(oldTotal) else "")}} -title "<name> uses Empowered Spell!" -desc "When you roll damage for a spell, you can spend 1 sorcery point to reroll a number of the damage dice up to your Charisma modifier (minimum of one). You must use the new rolls.  
  
You can use Empowered Spell even if you have already used a different Metamagic option during the casting of the spell. *(PHB 102)*" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -f "Old Dice|{{oldDice}} = ``{{oldTotal}}``" -f "Rerolled Dice|{{str(rerollDice)}}" -f "Difference|{{rerollDice.total}} - {{oldTotal}} = ``{{sign+str(rerollDice.total - int(oldTotal))}}``" -color <color>```