**Timer v1.0.0**  
*By Toothless#7854*  
  
Displays an embed which disappears after an allotted amount of time. When called without arguments, displays a help page on how to use the alias. This serves as a simple example of the new ``-t`` flag for embeds.  
  
```py  
!alias timer embed  
{{set("validTime", 1 if "%1%".isdigit() else 0)}}  
{{set("time", int("%1%") if validTime else 60)}}  
-title "Timer: {{"Set to %1% seconds!" if validTime else "[ERR] Invalid Time Input"}}"  
-desc "{{"This embed will disappear when the alloted time is up." if validTime else "``!timer <<time>>``\nCreates an embed which expires after an allotted time (in seconds)."}}"  
-footer "Timer v1.0.0 | !timer for more info"  
-t {{time}}  
```