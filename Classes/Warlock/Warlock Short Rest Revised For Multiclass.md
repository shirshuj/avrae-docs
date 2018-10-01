**Warlock Short Rest (revised for Multiclass)**  
*By TauNeutrino#3670 with some credit to Toothless#7854*  
  
**Note:** requires a cvar called ``WarlockLevel`` if you're multiclassing warlock and using a non-dicecloud character!  
  
```py  
!alias wsr embed  
{{set("splevel",min(ceil(int(WarlockLevel if exists("WarlockLevel") else level)/2),5))}}  
{{set("numSlots", 1 if WarlockLevel <= 1 else 2 if WarlockLevel < 11 else 3 if WarlockLevel < 17 else 4)}}  
{{set("levelName", "1st" if splevel == 1 else "2nd" if splevel == 2 else "3rd" if splevel == 3 else "4th" if splevel == 4 else "5th" if splevel == 5 else "")}}  
{{set_slots(splevel, min(numSlots + get_slots(splevel), get_slots_max(splevel)))}}  
-title "<name> regains {{numSlots}} Warlock Spell Slots!"  
-f "{{levelName}} Level | {{'◉'*get_slots(splevel) + '〇'*(get_slots_max(splevel)-get_slots(splevel))}}"  
-color <color>  
```