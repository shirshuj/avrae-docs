**Bard, College of Swords: Mobile Flourish**  
*By Ninja Bob#1827*  
  
Subtracts 1 from Bardic Inspiration counter, rolls additional damage, and calculates total distance pushed.  
```py  
!alias mf embed   
{{set("counter", "Bardic Inspiration")}} {{set("lvl", BardLevel)}}   
{{set("bd", "d6" if lvl < 5 else "d8" if lvl < 10 else "d10" if lvl < 15 else "d12")}}}   
{{mod_cc(counter, -1, True)}}  
{{(set("ans",(vroll(str(bd)))))}}  
-title "<name> uses Mobile Flourish!"   
-desc "You can expend one use of your Bardic Inspiration to cause the weapon to deal extra damage to the target you hit. The damage equals the number you roll on the Bardic Inspiration die. You can also push the target up to 5 feet away from you, plus a number of feet equal to the number you roll on that die. You can then immediately use your reaction to move up to your walking speed to an unoccupied space within 5 feet of the target."   
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"  
-f "Additional Damage | {{ans}}"  
-f "Target Pushed | {{ans.total+5}} ft."  
-footer "College of Swords | XGE 15 - 16" -color <color>  
```