**Shield Master shove**  
Prints out an embed  with some flavor text describing the shove (which you can change as you see fit) and also includes your characters athletics roll, displayed as the opponents DC for their acrobatics or athletics.  
  
```  
!alias shove embed -title "<name> shoves the enemy with his shield!" -desc "The opponent needs to make a **Strength (Athletics)** or **Dexterity (Acrobatics)** **DC {1d20 + strengthMod + proficiencyBonus}**. If they fail they fall prone or are knocked back 5 feet."  
```