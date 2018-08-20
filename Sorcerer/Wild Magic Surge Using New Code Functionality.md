**Wild magic surge using new code functionality.**  
*By Brinjal#4037.*   
A way to roll a Wild Magic Sorcerer's wild magic surges in style. Adding -thumb "<image>" on the end is optional.  
```!alias surge embed -title "Wild Magic Surge!" -desc "Rolling for wild magic surge.  
{{set("roll",roll("1d20"))}}{{"1d20 (" + str(roll) + ")\nNo wild magic surge." if roll > 1 else "1d20: (**1**) \n**Wild magic surge:** 1d100 (" + str(roll("1d100"))+")"}}"```