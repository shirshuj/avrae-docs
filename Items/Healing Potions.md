**Healing Potions**  
*By @sam#6556.*  
```  
!alias healingpot  
embed {{set("healmod", str(10 if %1%==4 else 8 if %1%==3 else 4 if %1%==2 else 2))}}  
{{set("heal", roll(healmod+"d4 + "+("20" if healmod=="10" else healmod)))}}  
{{set("potname",("" if %1%==1 else "Greater " if %1%==2 else "Superior " if %1%==3 else "Supreme "))}}  
-title "<name> uses a Potion of {{potname}}Healing"  
-desc "<name> drinks a Potion of {{potname}}Healing and regains **{{healmod+"d4 + "+("20" if healmod=="10" else healmod)}} ({{heal}})** hitpoints."```GN  
And the version which uses !g hp for ease of copy and paste (You can change `!g hp` to `!i hp <name>` for init): ```  
!alias healingpot multiline  
!embed {{set("healmod", str(10 if %1%==4 else 8 if %1%==3 else 4 if %1%==2 else 2))}} {{set("heal", roll(healmod+"d4 + "+("20" if healmod=="10" else healmod)))}} {{set("potname",("" if %1%==1 else "Greater " if %1%==2 else "Superior " if %1%==3 else "Supreme "))}} -title "<name> uses a Potion of {{potname}}Healing" -desc "<name> drinks a Potion of {{potname}}Healing and regains **{{healmod+"d4 + "+("20" if healmod=="10" else healmod)}} ({{heal}})** hitpoints."  
!g hp mod {{heal}}  
```