**Necrotic Shroud**  
*By ShadowPrince#8900 and Richard P.#0666*  
  
Fallen Aasimer Racial Ability!  
  
REQUIRES: ``!cc create "Necrotic Shroud" -type bubble -min 0 -max 1 -reset long``  
```py  
!alias shroud embed {{set("counter", "Necrotic Shroud")}} {{set("valid",cc_exists(counter) and get_cc(counter)>0)}} -title "<name> uses Necrotic Shroud!" -desc "{{"You do not have this ability." if not cc_exists(counter) else "You unleash the divine energy within yourself, causing your eyes to turn into pools of darkness and two skeletal, ghostly, flightless wings to sprout from your back. The instant you transform, other creatures within 10 feet of you that can see you must each succeed on a Charisma saving throw DC "+str(8+proficiencyBonus+charismaMod)+" or become frightened of you until the end of your next turn. Your transformation lasts for 1 minute or until you end it as a bonus action. During it, once on each of your turns, you can deal <level> extra necrotic damage to one target when you deal damage to it. " if valid else "The channel fails, as they need to have long rest before channeling again."}}" {{mod_cc(counter,-1,True) if valid else ""}} -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter)) if cc_exists(counter) else "*None*"}}" -thumb <image> -color <color>  
```