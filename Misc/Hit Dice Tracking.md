**Hit Dice Tracking**  
*By BetaBear#0213.*  
This is to automatically add HP during a short rest and keep track of the hit die with a custom counter. The alias rolls the hit die, adds it to the character sheet, and subtracts the used die from the cc.  
  
First create a custom counter for your hit die, I titled mine "hd"  
`!cc create hd -reset none -max <level> -min 0`  
Then make a cvar for your hit die as well  
`!cvar hd d10` (or whatever it is for your character; it's important not to include the 1)  
  
Then create the alias:  
```  
!alias shortrest  multiline  
!embed {{set("heal",(roll("%1%"+hd)+%1%*constitutionMod))}} -title "<name> rests for a bit." -desc "<name> relaxes, spending %1% hit die and recovering {{heal}} hit points."  
!cc hd -%1%  
!g hp mod {{heal}}  
!g sr```