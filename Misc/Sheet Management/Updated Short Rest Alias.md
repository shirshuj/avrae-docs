**Updated Short Rest Alias**  
*By silverbass#2407*  
  
Taking inspiration from Toothless#7854 and his hit dice script, I now also display amount healed. This will be helpful for anyone with the durable feat. This one bears a lot in common with Toothless's hit dice alias. Hopefully we'll stop having to push these out and just have hitdice be tracked natively by Avrae.  
  
```!servalias shortrest multiline  
!embed {{set("diceused", min(get_cc("Hit Dice"), %1%)) if %1% > int(get_cc("Hit Dice")) else set("diceused",%1%)}}{{set("roll",(str(diceused)+str(hd))+"+"+str(diceused*constitutionMod))}}{{set("vheal", vroll(roll))}}{{set("heal", vheal.total)}}{{set_hp(min(hp, heal + currentHp))}}{{set_hp(min(hp, heal+ currentHp))}} -title "<name> rests for a bit." -desc "<name> relaxes, spending {{diceused}} hit die and recovering {{heal}} hit points." -f "Healing Recieved|{{str(vheal)}}"  -f "Current HP: | {{min(hp, (heal + currentHp))}}/{{hp}}{{set_hp(min(hp, (heal + currentHp)))}}" -f "Hit Dice | {{mod_cc("Hit Dice", -diceused)}}{{get_cc("Hit Dice")}}/{{get_cc_max("Hit Dice")}} {{str(hd)}}" -color <color>  
!g sr -h```  
  
**Use With:** ``!shortrest <#>`` where <#> is how many dice you want to use.  
**Note to DMs:** Set this up as a servalias and your players will be able to use it as long as the have hit dice set up.  
  
  
``!alias longrest g {{set_cc("Hit Dice", min(get_cc_max("Hit Dice"),(get_cc("Hit Dice")+(get_cc_max("Hit Dice")/2))))}} lr``  
  
**How To Use:** ``!longrest``