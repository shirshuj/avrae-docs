**Green-Flame Blade and Booming Blade!**  
*By silverbass#2407*  
  
```py  
!snippet gfb -d "{{"0" if level<5 else ("1" if level<11 else "2" if level<17 else "3")+"d8"}} [fire]" -f "Green-Flame Blade | On a hit, the target suffers the attack's normal effects{{", the melee attack deals an extra "+("1" if level<11 else "2" if level<17 else "3")+"d8 fire damage to the target" if level>=5 else""}}, and green fire leaps from the target to a different creature of your choice that you can see within 5 feet of it. The second creature takes {{vroll(str((("1" if level<11 else "2" if level<17 else "3") +"d8 + " if level>=5 else"") + str(intelligenceMod) +" [fire]"))}} fire damage." -title "[charname] casts Green-Flame Blade with a [aname] at [target]"  
```  
  
```py  
!snippet bb -d "{{"0" if level<5 else ("1" if level<11 else "2" if level<17 else "3")+"d8"}} [thunder]" -f "Booming Blade | On a hit, the target suffers the attack's normal effects{{", the melee attack deals an extra "+("1" if level<11 else "2" if level<17 else "3")+"d8 thunder damage to the target" if level>=5 else""}}, and it becomes sheathed in booming energy until the start of your next turn. If the target willingly moves before then, it immediately takes {{vroll(str(("1" if level<5 else "2" if level<11 else "3" if level<17 else "4")+"d8 [thunder]"))}} damage, and the spell ends." -title "[charname] casts Booming Blade with a [aname] at [target]"  
```  
  
**Use With:** ``![a | i a target] <weapon> [bb | gfb]``  
  
**Edit:** The ``thunder`` damage in ``gfb`` has been corrected to ``fire``.