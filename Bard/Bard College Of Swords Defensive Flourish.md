**Bard, College of Swords: Defensive Flourish**  
*By Ninja Bob#1827*  
  
Subtracts 1 from "Bardic Inspiration" counter, rolls additional damage, and calculates modified AC.  
```py  
!alias df embed   
{{set("counter", "Bardic Inspiration")}} {{set("lvl", BardLevel)}}   
{{set("bd", "d6" if lvl < 5 else "d8" if lvl < 10 else "d10" if lvl < 15 else "d12")}}}   
{{mod_cc(counter, -1, True)}}  
{{(set("ans",(vroll(str(bd)))))}}  
-title "<name> uses Defensive Flourish!"   
-desc "You can expend one use of your Bardic Inspiration to cause the weapon to deal extra damage to the target you hit.  The damage equals the number you roll on the Bardic Inspiration die.  You also add the number rolled to your AC until the start of your next turn"   
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"  
-f "Additional Damage | {{ans}}"  
-f "Boosted AC | {{ans.total+armor}}"  
-footer "College of Swords | XGE 15 - 16" -color <color>  
```