**Lucky Feat**  
*By Brinjal#4037 and zhu.exe#4211.*  
Create counter: `!cc create "Luck Points" -min 0 -max 3 -reset long -type bubble`  
Call `!lucky` to roll a d20, use the cc, and print the new roll.  
```md  
!alias lucky embed -title "What a stroke of luck!" -desc "Using the **lucky** feat, <name> can reroll an attack roll, ability check, saving throw, or an opponent's attack roll and choose which roll to use." -f "Roll|{{str(vroll('1d20'))+mod_cc("Luck Points",-1) if get_cc("Luck Points") >0 else "Never mind! "+name+" has no remaining luck points and must take a long rest to use the lucky feat again!"}}" -footer "Remaining Luck Points: {{str(get_cc("Luck Points"))}}" -thumb <image>  
```