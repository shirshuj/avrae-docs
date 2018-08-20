**Bard, College of Swords: Slashing Flourish**  
*By Ninja Bob#1827*  
  
Subtracts 1 from Bardic Inspiration counter and rolls additional damage.  
```py  
!alias sf embed   
{{set("counter", "Bardic Inspiration")}} {{set("lvl", BardLevel)}}   
{{set("bd", "d6" if lvl < 5 else "d8" if lvl < 10 else "d10" if lvl < 15 else "d12")}}}   
{{mod_cc(counter, -1, True)}}  
{{(set("ans",(vroll(str(bd)))))}}  
-title "<name> uses Slashing Flourish!"   
-desc "You can expend one use of your Bardic Inspiration to cause the weapon to deal extra damage to the target you hit and to any other creature of your choice that you can see within 5 feet of you. The damage equals the number you roll on the Bardic Inspiration die."   
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"  
-f "Additional Damage to targets within 5 feet | {{ans}}"  
-footer "College of Swords | XGE 15 - 16" -color <color>  
```