**Another Way to run Custom Skills!** "General"  
*By silverbass#2407*  
  
Rather than using an actual Alias, Toothless#7854 showed me a trick to adjust normal ability checks. You can turn these into Aliases for easy use. I'll be using an Intelligence (Tinkering) check for someone with *expertise* for this example.  
```  
!alias lockpick c intelligence -b {{proficiencyBonus*2}} -title "<name> makes an Intelligence (Tinkering) check!"  
```  
  
**Use With:** ``!tinker``  
  
Note you may need to change the check specified to the ability check relavent for your skill/tool. For example, I have Dexterity (Tinkering) checks as well. Also, remove the ``*2`` on characters that only have proficiency, not expertise, like so:  
  
```  
!alias tinker c intelligence -b <proficiencyBonus> -title "<name> makes an Intelligence (Tinkering) check!"  
```