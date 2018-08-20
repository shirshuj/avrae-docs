**Aasimar's Healing Hands, revamped to work well in initiative!**  
*By mostly Croebh#5603 with a sprinkle of silverbass#2407*  
  
Requires: `!cc create "Healing Hands" -min 0 -max 1 -reset long -type bubble`  
Use With: `!aasimar-hh [target=self]`  
  
```  
!alias aasimar-hh embed   
{{c,cc,a=combat(),"Healing Hands","&*&" if "&*&" else ""}}  
{{v=cc_exists(cc) and get_cc(cc)>0}}  
{{t=c.get_combatant(a) if c and a else None}}  
-title "<name> {{"channels" if v else "attempts to channel"}} their Healing Hands!"  
-desc "{{"You do not have this ability" if not cc_exists(cc) else "As an action, you can touch a creature and cause it to regain "+str(level)+" hit points." if v else "You must complete a long rest before you can use this again."}}"{{mod_cc(cc,-1) if v else ""}}  
-f "{{cc}}|{{cc_str(cc) if cc_exists(cc) else "*None*"}}"   
{{'-f "Healing Received|'+str(level)+'"' if v else ""}}  
{{(t.set_hp(min(t.maxhp,level+t.hp)) if t and t.hp else t.mod_hp(+level) if t else set_hp(min(hp,level+get_hp())) if not a else "") if v else ""}}  
{{'-f "'+(t.name if t else a.title() if a else name)+'|'+(t.hp_str() if t else "+"+str(level) if a else str(get_hp())+"/"+str(hp))+'"' if v else ""}}  
-color <color> -thumb <image>  
```