**Font of Magic**  
*By Croebh#5603 I think? IDK all I did was fix the type stuff.*  
  
```py  
!alias font embed  
{{set("a","Sorcery Points")}}  
{{set("b",1 if "%1%" == "create" else 2 if "%1%"=="spend" else 0)}}  
{{set("c",2 if "%2%"=="1" else 3 if "%2%"=="2" else 5 if "%2%"=="3" else 6 if "%2%"=="4" else 7 if "%2%">="5" else 0)}}  
{{set("s",min((5 if b==1 else 9),%2%))}}  
{{set("x","st" if s==1 else "nd" if s==2 else "rd" if s==3 else "th")}}  
-title "<name> invokes the Font of Magic - {{"Create "+str(s)+x+" Level Slot" if b==1 else "Spend "+str(s)+x+" Level Slot" if b==2 else "Uuuh..."}}"  
{{("" if mod_cc(a,-c,True) else "")+(""  if set_slots(s, int(get_slots(s))+1) else "") if b==1 else ("" if mod_cc(a,+s) else "")+("" if use_slot(s) else "") if b==2 else ""}}  
-f "{{a}} ({{"-"+str(c) if b==1 else "+"+str(s) if b==2 else ""}})|{{'◉'*get_cc(a) + '〇'*(get_cc_max(a)-get_cc(a))}}"  
-f "{{s}}{{x}} Level Slots ({{"+1" if b==1 else "-1" if b==2 else ""}})|{{'◉'*get_slots(s) + '〇'*(get_slots_max(s)-get_slots(s))}}"  
-desc "{{"**Creating Spell Slots.** You can transform unexpended sorcery points into one spell slot as a bonus action on your turn. The created spell slots vanish at the end of a long rest. You can create spell slots no higher in level than 5th.\n\nCreating a "+str(s)+x+" Level Slot, spending "+str(c)+" Sorcery Points." if b==1 else "**Converting a Spell Slot to Sorcery Points.** As a bonus action on your turn, you can expend one spell slot and gain a number of sorcery points equal to the slot's level.\n\nSpending a "+str(s)+x+" Level Slot, creating "+str(s)+" Sorcery Points." if b==2 else "Way to spell things properly. Not!"}}"  
-footer "Sorcerer | PHB 101" -color <color> -thumb <image>  
```