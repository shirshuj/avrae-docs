**Sorcerer's Twinned Spell**  
*By silverbass#2407*  
  
Requires: `Sorcery Points` cc  
Use with: `!sorc-twin [lvl=1]`  
```  
!alias sorc-twin embed {{set("cc", "Sorcery Points")}}   
{{x=int("&1&") if "&1&".isdigit() else 1}}  
{{v=cc_exists(cc) and get_cc(cc) >= x}}  
-title "<name> {{"spends "+str(x)+" Sorcery Point"+("s" if x>1 else "")+" to use" if v else "tries to use"}} Twinned Spell!"   
-desc "{{"When you cast a spell that doesn't have a range of self and is incapable of targeting more than one creature at the spell's current level, you can spend a number of sorcery points equal to the spell's level to target a second creature in range with the same spell (1 sorcery point if the spell is a cantrip)." if v else "You must finish a short or long rest before you can use it again." if cc_exists(cc) else "You do not have this ability."}}"  
{{mod_cc(cc, -x)  if v else ""}}  
{{"-f \""+cc+"|"+('◉'*get_cc(cc) + '〇'*(get_cc_max(cc)-get_cc(cc)) if get_cc_max(cc)<6 else str(get_cc(cc))+"/"+str(get_cc_max(cc)))+"\"" if cc_exists(cc) else "*None*"}}  
-footer "Sorcerer | PHB 102"  
-color <color> -thumb <image>  
```