**Warlock Short Rest**  
*by Toothless#7854*  
  
Restores Warlock spell slots and displays the number of spell slots left.  
  
Typically, you can ``!csettings srslots true`` to have your spell slots restore on a short rest. However, that refreshes all of your spell slots instead of just your Warlock ones, which makes it challenging for multiclassing. You can use this alias to only restore those from your Warlock multiclass.  
  
If you are using a non-DiceCloud sheet, type the following command. You must run this command every time you take a level in Warlock, otherwise it will not update. Replace ``$level$`` with your current Warlock level.  
  
```GN  
!cvar WarlockLevel $level$```GN  
```py  
!alias gsrw embed  
{{set("level",min(ceil(WarlockLevel/2),5))}}  
{{set("numSlots", 1 if WarlockLevel <= 1 else 2 if WarlockLevel < 11 else 3 if WarlockLevel < 17 else 4)}}  
{{set("levelName", "1st" if level == 1 else "2nd" if level == 2 else "3rd" if level == 3 else "4th" if level == 4 else "5th" if level == 5 else "")}}  
{{set_slots(level, numSlots)}}  
-title "<name> regains {{numSlots}} Warlock Spell Slots!"  
-f "{{levelName}} Level | {{'◉'*get_slots(level) + '〇'*(get_slots_max(level)-get_slots(level))}}"  
-thumb <image>  
-color <color>  
```