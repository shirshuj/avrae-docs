**Revised Hit Dice Tracking**  
*By Croebh#5603.*  
  
Hit Dice resets on long rest, doesnt go above max hp, and does the healing and hit dice modifying inside the first embed, and doesn't go below 0 hit dice, and doesn't heal if you run out of hit dice  
  
`!cc create "Hit Dice" -reset long -max <level> -min 0`  
`!cvar hd d8`  
  
```!alias shortrest multiline  
!embed {{set("diceused", min(get_cc("Hit Dice"), %1%)) if %1% > int(get_cc("Hit Dice")) else set("diceused",%1%)}}{{set("heal",(roll(str(diceused)+str(hd))+(diceused*constitutionMod)))}} -title "<name> rests for a bit." -desc "<name> relaxes, spending {{diceused}} hit die and recovering {{heal}} hit points." -f "Current HP: | {{min(hp, (heal + currentHp))}}/{{hp}}{{set_hp(min(hp, (heal + currentHp)))}}" -f "Hit Dice | {{mod_cc("Hit Dice", -diceused)}}{{get_cc("Hit Dice")}}/{{get_cc_max("Hit Dice")}} {{str(hd)}}"  
!g sr```