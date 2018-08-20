**Infernal Legacy Spells!** "Tiefling"  
*By silverbass#2407*  
  
Infernal Legacy grants tieflings the ability to cast the *thaumaturgy* cantrip, along with *hellish rebuke* at level 3 and *darkness* at level 5, once per long rest for each. This set of aliases and custom counters can facilitate that!  
  
``!cc create "Hellish Rebuke" -reset long -min 0 -max 1 -type bubble``  
```  
!alias rebuke multiline  
!embed {{set("counter", "Hellish Rebuke")}} {{mod_cc(counter, -1, True)}} -title "<name> invokes their Infernal Legacy!" -desc "<name> casts {{counter}}!" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -color <color>  
!cast "Hellish Rebuke" -i  
```  
**Use With:** ``!rebuke``  
  
``!cc create "Darkness" -reset long -min 0 -max 1 -type bubble``  
```  
!alias darkness multiline  
!embed {{set("counter", "Darkness")}} {{mod_cc(counter, -1, True)}} -title "<name> invokes their Infernal Legacy!" -desc "<name> casts {{counter}}!" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -color <color>  
!cast Darkness -i  
```  
**Use With:** ``!darkness``  
  
Goals: Make this work using ``!i cast`` instead of ``!cast``. For now, ``!i cast`` causes issues since *Hellish Rebuke* is a reaction, and thus is usually used off-turn.  
**Note to DMs:** You can make these ``!servalias`` instead of just ``!alias`` as long as you have your tiefling make the custom counters.