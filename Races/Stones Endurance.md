**Stone's Endurance!** "Goliath"  
*By one of my players!*  
  
The goliath trait that allows you to reduce damage! This alias doesn't actually adjust hp or reduce damage; that much is left to the DM to actually apply. It just rolls dice and looks pretty!  
  
``!cc create "Stone's Endurance" -min 0 -max 1 -type bubble -reset short``  
```  
!alias stone embed {{set("counter", "Stone's Endurance")}} {{mod_cc(counter, -1, True)}} {{set("reduction", vroll("1d12+"+str(constitutionMod)))}} -title "<name> uses {{counter}}!" -desc "You can focus yourself to occasionally shrug off injury. When you take damage, you can use your reaction to roll a d12. Add your Constitution modifier to the number rolled, and reduce the damage by that total. After you use this trait, you can't use it again until you finish a short or long rest." -f "Damage Reduced|{{str(reduction)}}" -f "{{counter}}|〇" -color <color>  
```  
  
**Use With:** ``!stone``