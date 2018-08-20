**Tiefling and Drow Racials**  
*By silverbass#2407*  
  
Needs custom counters:   
**Drow and Tiefling:** `!cc create Darkness -min 0 -max 1 -reset long -type bubble`  
**Drow Only:** `!cc create "Faerie Fire" -min 0 -max 1 -reset long -type bubble`  
**Tiefling Only:** `!cc create "Hellish Rebuke" -min 0 -max 1 -reset long -type bubble`  
  
```  
!alias tiefling multiline  
!embed {{set("counter", "Hellish Rebuke" if "%1%".lower() in "hellish rebuke" else "Darkness" if "%1%".lower() in "darkness" else "")}}{{set("v",cc_exists(counter) and get_cc(counter)>0)}}{{mod_cc(counter, -1, True) if v else ""}} -title "<name> {{"channels" if v else "tries to channel"}} their Infernal Legacy!" -desc "{{"You know the thaumaturgy cantrip. Once you reach 3rd level, you can cast the hellish rebuke spell as a 2nd-level spell; you must finish a long rest in order to cast the spell again using this trait. Once you reach 5th level, you can also cast the darkness spell; you must finish a long rest in order to cast the spell again using this trait. Charisma is your spellcasting ability for these spells." if not cc_exists(counter) else name+" casts "+counter if v else "You must finish a long rest before you can use it again."}}" {{"-f \""+counter+"|"+'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))+"\"" if cc_exists(counter) else ""}} -color <color> -thumb <image> -footer "Race | Tiefling"  
{{"!cast \""+counter+"\" -i" if v else ""}}  
```GN  
```  
!alias drow multiline  
!embed {{set("counter", "Faerie Fire" if "%1%".lower() in "faerie fire" else "Darkness" if "%1%".lower() in "darkness" else "")}}{{set("v",cc_exists(counter) and get_cc(counter)>0)}}{{mod_cc(counter, -1, True) if v else ""}} -title "<name> {{"uses" if v else "tries to use"}} their Drow Magic!" -desc "{{"You know the dancing lights cantrip. When you reach 3rd level, you can cast the faerie fire spell once per day; you must finish a long rest in order to cast the spell again using this trait. When you reach 5th level, you can also cast the darkness spell once per day; you must finish a long rest in order to cast the spell again using this trait. Charisma is your spellcasting ability for these spells." if not cc_exists(counter) else name+" casts "+counter if v else "You must finish a long rest before you can use it again."}}" {{"-f \""+counter+"|"+cc_str(counter)+"\"" if cc_exists(counter) else ""}} -color <color> -thumb <image> -footer "Race | Drow"  
{{"!cast \""+counter+"\" -i" if v else ""}}  
```