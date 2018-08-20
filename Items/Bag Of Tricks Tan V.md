**Bag of Tricks, Tan v1.1.0**  
*By Toothless#7854, inspired by Croebh#5603*  
  
My own version of the Bag of Tricks, for Tan. Added bugfixes and book / page number in footer. Usage is ``!bag``. Automatically subtracts a use, rolls a die, then displays the monster rolled.  
  
```py  
!cc create "Bag of Tricks, Tan" -min 0 -max 3 -type bubble -reset long  
```  
```py  
!alias tan embed {{set("counter", "Bag of Tricks, Tan")}} {{mod_cc(counter, -1, True)}} {{set("die", vroll("1d8"))}} {{set("table", ["Jackal", "Ape", "Baboon", "Axe Beak", "Black Bear", "Giant Weasel", "Giant Hyena", "Tiger"])}} -title "<name> uses their Bag of Tricks, Tan!" -desc "You can use an action to pull a fuzzy object from the bag and throw it up to 20 feet. When the object lands, it transforms into a creature you determine by rolling a d8 and consulting the table that corresponds to the bag's color. See the Monster Manual for the creature's statistics.  
  
__**d8 — Creature**__  
1 — Jackal  
2 — Ape  
3 — Baboon  
4 — Axe beak  
5 — Black bear  
6 — Giant weasel  
7 — Giant hyena  
8 — Tiger" -f "d8|{{str(die)}}" -f "Creature|{{table[die.total-1]}}" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -footer "Treasure | DMG 151" -color <color>  
```