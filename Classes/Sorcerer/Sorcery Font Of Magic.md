**Sorcery Font of Magic**  
*by Croebh#5603*  
  
An alias to use the Font of Magic feature of Sorcerers to create/spend spell slots and sorcery points. Doesn't allow you to create slots above level 5. (Ignore the amount of sorcery points and spell slots in the image, its a test character)  
  
`!cc create "Sorcery Points" -max level -min 0 -reset long`  
  
```python  
!alias font embed  
{{counter,t,T='Sorcery Points',1 if '&1&' in 'create' else 2 if '&1&' in 'spend' else 0,2 if "&2&"=="1" else 3 if "&2&"=="2" else 5 if "&2&"=="3" else 6 if "&2&"=="4" else 7 if "&2&">="5" else 0}}{{s=min((5 if t==1 else 9),int("&2&" if '&' not in "&2&" else 0))}}
{{verb = "st" if s==1 else "nd" if s==2 else "rd" if s==3 else "th"}}
-title "Font of Magic{{" - Create "+str(s)+verb+" Level Slot" if t==1 else " - Spend "+str(s)+verb+" Level Slot" if t==2 else ""}}"  
{{(str(mod_cc(counter,-T,True))+str(set_slots(s, int(get_slots(s))+1))).replace('None','') if t==1 else (str(mod_cc(counter,+s))+str(use_slot(s))).replace('None','') if t==2 else ""}}  
-f "{{counter}} {{("(-"+str(T) if t==1 else "(+"+str(s) if t==2 else "")+')'}}|{{cc_str(counter)}}"  
-f "{{s}}{{verb}} Level Slots ({{"+1" if t==1 else "-1" if t==2 else ""}})|{{slots_str(s)}}"  
-desc "{{"**Creating Spell Slots.** You can transform unexpended sorcery points into one spell slot as a bonus action on your turn. The created spell slots vanish at the end of a long rest. You can create spell slots no higher in level than 5th.\n\nCreating a "+str(s)+verb+" Level Slot, spending "+str(T)+" Sorcery Points." if t==1 else "**Converting a Spell Slot to Sorcery Points.** As a bonus action on your turn, you can expend one spell slot and gain a number of sorcery points equal to the slot's level.\n\nSpending a "+str(s)+verb+" Level Slot, creating "+str(s)+" Sorcery Points." if t==2 else "`!font create #` to create a slot with Sorcery Points,\n `!font spend #` to spend a slot to gain Sorcery Points"}}"  
-footer "Font of Magic | PHB.101"  
```  
  
**How to Use:**  
`!font [create|spend] <level>`  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/391781561411960832/unknown.png)
