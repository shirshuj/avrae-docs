**Warlock Casting Helper**  
*By Croebh#5603*  
  
Helpful alias for casting spells with Warlock spell slots. Tries each slot up till 5 to see if you have slots, and appends a -phrase for spells that allow it.  
  
`!wcast [spell]`  
  
```GN  
!alias wcast cast {{set("level","1" if get_slots(1) else "2" if get_slots(2) else "3" if get_slots(3) else "4" if get_slots(4) else "5")}} %1% -l {{level}} -phrase "using a Level {{level}} spell slot"```