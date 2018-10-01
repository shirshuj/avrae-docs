**Superiority Dice Snippet**  
*By Croebh#5603*  
A snippet to add Superiority Dice to damage rolls, while keeping track of total dice.  
`![a|i a <target>] <weapon> superiority [args...]`  
  
`!cc create "Superiority Dice" -reset short -max {{4 if level <= 6 else 5 if level <= 14 else 6}} -min 0`  
`!snippet superiority {{str("-d 1d8 -phrase \"with Superiority\"") if get_cc("Superiority Dice") > 0 else ""}}{{mod_cc("Superiority Dice", -1) if get_cc("Superiority Dice") > 0 else ""}}`