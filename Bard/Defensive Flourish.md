**Defensive Flourish**  
*By silverbass#2407 and gabrielcaetano#3494*  
  
```  
!alias df multiline  
!embed  {{set("counter", "Inspiration")}}{{set("v",cc_exists(counter) and get_cc(counter)>0)}}{{set("lvl",int(BardLevel) if exists("BardLevel") else level)}} {{set("bd", "d6" if lvl < 5 else "d8" if lvl < 10 else "d10" if lvl < 15 else "d12")}}} {{mod_cc(counter, -1, True) if v else ""}}{{(set("ans",(vroll(str(bd)))))}} -title "<name> {{"uses" if v else "tries to use"}} Defensive Flourish!" -desc "{{"You can expend one use of your Bardic Inspiration to cause the weapon to deal extra damage to the target you hit.  The damage equals the number you roll on the Bardic Inspiration die.  You also add the number rolled to your AC until the start of your next turn" if v else "You must complete a "+("long" if lvl<5 else "short")+" rest before you can use this feature again."}}" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" {{"-f \"Additional Damage |"+str(ans)+"\"" if v else ""}} {{"-f \"New AC |"+str(ans.total+armor)+"\"" if v else ""}} -footer "College of Swords | XGE 15 - 16" -color <color>  
{{"!i opt \"<name>\" -armor "+str(ans.total+armor)+"\"" if v else ""}}  
```  
  
**Requires:** a cc called "Inspiration"  
**Use with:** `!df`