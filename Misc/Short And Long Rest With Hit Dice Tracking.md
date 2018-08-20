**Short and Long rest with Hit Dice Tracking**  
*By silverbass#2407 and Croebh#5603*  
Regain half your total hit dice on long rest, doesnt go above max hp, and does the healing and hit dice modifying inside the first embed, and doesn't go below 0 hit dice, and doesn't heal if you run out of hit dice.  
  
`!cc create "Hit Dice" -reset none -max <level> -min 0 -type bubble`  
`!cvar hd d8`  
   
```python  
!alias shortrest multiline  
!embed {{set("diceused", min(get_cc("Hit Dice"), %1%)) if %1% > int(get_cc("Hit Dice")) else set("diceused",%1%)}}{{set("heal",(roll(str(diceused)+str(hd))+(diceused*constitutionMod)))}} -title "<name> rests for a bit." -desc "<name> relaxes, spending {{diceused}} hit die and recovering {{heal}} hit points." -f "Current HP: | {{min(hp, (heal + currentHp))}}/{{hp}}{{set_hp(min(hp, (heal + currentHp)))}}" -f "Hit Dice | {{mod_cc("Hit Dice", -diceused)}}{{get_cc("Hit Dice")}}/{{get_cc_max("Hit Dice")}} {{str(hd)}}" -color <color>  
!g sr  
```GN  
```python  
!alias longrest g {{set_cc("Hit Dice", min(get_cc_max("Hit Dice"),(get_cc("Hit Dice")+(get_cc_max("Hit Dice")/2))))}} lr  
```  
  
**How To Use:**  
`!shortrest <#-dice-used>`   
`!longrest`