**Lucky Feat, v2.0**  
*By newtim#1227, Brinjal#4037, and zhu.exe#4211.*  
```GN  
!embed -title "What a stroke of luck!" -desc "Using the lucky feat, <name> can reroll an attack roll, ability check, saving throw, or an opponent's attack roll and choose which roll to use." -f "Roll|{{str(vroll('1d20'))+("" if mod_cc("Luck Points",-1) else "") if get_cc("Luck Points") >0 else "Never mind! "+name+" has no remaining luck points and must take a long rest to use the lucky feat again!"}}" -footer "Remaining Luck Points: {{str(get_cc("Luck Points"))}}" -thumb <image>```  
  
Prereqs before use: A cc named "Luck Points".