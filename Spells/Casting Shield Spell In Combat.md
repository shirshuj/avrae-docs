**Casting Shield Spell in Combat!**  
```  
!alias cast-shield multiline  
!embed {{slots=[get_slots(i) for i in range(1,10)]}}{{cast=[i for i in range(1,10) if slots[i-1]]}}{{lvl=cast[0] if cast else 0}} -title "<name> {{"casts" if cast else "tries to cast"}} Shield!" -desc "{{"An invisible barrier of magical force appears and protects you. Until the start of your next turn, you have a +5 bonus to AC, including against the triggering attack, and you take no damage from magic missile." if cast else "You do not have any spell slots left."}}" {{use_slot(lvl) if cast else ""}} {{'-f "Spell Slots|`'+str(lvl)+'` '+'◉'*get_slots(lvl)+'〇'*(get_slots_max(lvl)-(get_slots(lvl)))+'"' if cast else ''}} -color <color> -thumb <image> {{c=combat()}} -f "Current AC|{{(c.me.ac+5 if c else armor+5) if cast else armor}}"  
{{"!i effect \""+name+"\" 0 Shield -ac +5" if cast and c else ""}}  
```  
  
WARNING: this alias will consume the spell slot for shield, and will upcast with a 2nd level slot if you are out of 1st... and a 3rd level slot if you are out of 2nd... etc....  
*this is intentional.*