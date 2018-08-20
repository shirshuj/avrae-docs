**Booming Blade / Green-Flame Blade**  
*By Toothless#7854*  
  
Rolls damage for *booming blade* and *green-flame blade*. Automatically calculates level and spellcasting mod.  
  
**Booming Blade**  
```py  
!snippet boom  
{{set("dice", 1 if level < 5 else 2 if level < 11 else 3 if level < 17 else 4)}}  
{{set("dmg", vroll(str(dice) + "d8 [thunder]"))}}  
{{"" if level < 5 else "-d \"" + str(dice - 1) + "d8 [thunder, boom]\""}}  
-f "Booming Blade | On a hit, if the target willingly moves before then, it immediately takes {{str(dmg)}} thunder damage."  
```  
**Green-Flame Blade**  
```py  
!snippet gfb  
{{set("mod", str(max(charismaMod, intelligenceMod)))}}  
{{set("dice", " " if level < 5 else "1d8" if level < 11 else "2d8" if level < 17 else "3d8")}}  
{{set("dmg", vroll(dice + (" + " if level >= 5 else "") + mod + " [fire]"))}}  
{{"" if level < 5 else "-d \"" + dice + " [fire, gfb]\""}}  
-f "Green-Flame Blade | On a hit, a different creature of your choice you can see within 5 feet of your target takes {{str(dmg)}} damage."  
```