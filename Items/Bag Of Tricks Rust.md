**Bag of Tricks, Rust**  
*By Richard P.#0666, inspired by Croebh#5603 and inspired and tweaked by Toothless#7854*  
  
An alias for the *bag of tricks, rust. Usage is ``!rust``. Automatically subtracts a use, rolls a die, then displays the monster rolled.  
  
```py  
!cc create "Bag of Tricks, Rust" -min 0 -max 3 -type bubble -reset long  
```GN  
```py  
!alias rust embed {{set("counter", "Bag of Tricks, Rust")}} {{mod_cc(counter, -1, True)}} {{set("die", vroll("1d8"))}} {{set("table", ["Rat", "Owl", "Mastiff", "Goat", "Giant Goat", "Giant boar", "Lion", "Brown bear"])}} -title "<name> uses their Bag of Tricks, Rust!" -desc "You can use an action to pull a fuzzy object from the bag and throw it up to 20 feet. When the object lands, it transforms into a creature you determine by rolling a d8 and consulting the table that corresponds to the bag's color. See the Monster Manual for the creature's statistics.  
  
__**d8 — Creature**__  
1 — Rat  
2 — Owl  
3 — Mastiff  
4 — Goat  
5 — Giant goat  
6 — Giant boar  
7 — Lion  
8 — Brown bear"  
-f "d8|{{str(die)}}" -f "Creature|{{table[die.total-1]}}" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -footer "Treasure | DMG 151" -color <color>```