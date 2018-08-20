**Green-Flame Blade**  
*By zhu.exe#4211.*  
This is a snippet you can append to any weapon you use for GFB, that autoscales to level. Change `intelligenceMod` to your spellcasting modifier. ```py  
!snippet gfb {{set("mod", intelligenceMod)}}{{"" if level < 5 else "-d 1d8[fire]" if 4 < level < 11 else "-d 2d8[fire]" if 10 < level < 17 else "-d 3d8[fire]"}} {{set('bonus', mod if level < 5 else vroll('1d8+'+str(mod)) if 4 < level < 11 else vroll('2d8+'+str(mod)) if 10 < level < 17 else vroll('3d8+'+str(mod)))}}-phrase "On a hit, green fire leaps from the target to a different creature of my choice within 5 feet, which takes {{bonus}} fire damage."  
```