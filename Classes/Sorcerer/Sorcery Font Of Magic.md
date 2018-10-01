**Sorcery Font of Magic**  
*by Croebh#5603*  
  
An alias to use the Font of Magic feature of Sorcerers to create/spend spell slots and sorcery points. Doesn't allow you to create slots above level 5. (Ignore the amount of sorcery points and spell slots in the image, its a test character)  
  
`!cc create "Sorcery Points" -max level -min 0 -reset long`  
  
```python  
!alias font embed  
{{set("a","Sorcery Points")}}  
{{set("b",1 if "%1%" == "create" else 2 if "%1%"=="spend" else 0)}}  
{{set("c",2 if "%2%"=="1" else 3 if "%2%"=="2" else 5 if "%2%"=="3" else 6 if "%2%"=="4" else 7 if "%2%">="5" else 0)}}  
{{set("s",min((5 if b==1 else 9),%2%))}}  
{{set("x","st" if s==1 else "nd" if s==2 else "rd" if s==3 else "th")}}  
-title "Font of Magic - {{"Create "+str(s)+x+" Level Slot" if b==1 else "Spend "+str(s)+x+" Level Slot" if b==2 else "Uuuh..."}}"  
{{mod_cc(a,-c,True)+set_slots(s, int(get_slots(s))+1) if b==1 else mod_cc(a,+s)+use_slot(s) if b==2 else ""}}  
-f "{{a}} ({{"-"+str(c) if b==1 else "+"+str(s) if b==2 else ""}})|{{'◉'*get_cc(a) + '〇'*(get_cc_max(a)-get_cc(a))}}"  
-f "{{s}}{{x}} Level Slots ({{"+1" if b==1 else "-1" if b==2 else ""}})|{{'◉'*get_slots(s) + '〇'*(get_slots_max(s)-get_slots(s))}}"  
-desc "{{"**Creating Spell Slots.** You can transform unexpended sorcery points into one spell slot as a bonus action on your turn. The created spell slots vanish at the end of a long rest. You can create spell slots no higher in level than 5th.\n\nCreating a "+str(s)+x+" Level Slot, spending "+str(c)+" Sorcery Points." if b==1 else "**Converting a Spell Slot to Sorcery Points.** As a bonus action on your turn, you can expend one spell slot and gain a number of sorcery points equal to the slot's level.\n\nSpending a "+str(s)+x+" Level Slot, creating "+str(s)+" Sorcery Points." if b==2 else "Way to spell things properly. Not!"}}"  
-footer "Font of Magic | PHB.101"  
```  
  
**How to Use:**  
`!font [create|spend] <level>`  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/391781561411960832/unknown.png)