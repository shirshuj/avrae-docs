**Warlock Spell Slot Snippet**  
*by matthileo#0735*  
  
Alternate version of the Warlock Slot alias as a snippet that  
1. Works if you multiclass with another spellcasting class.  
2. Works with !cast and !init cast eg. `!cast hex ws` `!i cast rebuke -t GOB1 ws`  
  
If not using DiceCloud, change `WarlockLevel` to `level`  
  
`!snippet ws {{set("level",min(ceil(WarlockLevel/2),5))}} -l {{level}} -phrase "using a Level {{level}} spell slot"`