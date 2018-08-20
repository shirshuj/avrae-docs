**Durable Feat!**  
*By silverbass#2407*  
  
Since the shortrest command now shows what the dice actually rolled, the durable feat can be used after the rest to apply the feat's benefits! This alias automatically applies the difference in hp!  
  
```  
!alias durable embed {{set("oldDice", "%1%")}} {{set("oldTotal", "%2%")}} -title "<name>'s makes use of their durability!" -desc "When you roll a Hit Die to regain hit points, the minimum number of hit points you regain from the roll equals twice your Constitution modifier (minimum of 2)." -f "Old Healing|{{oldDice+str(hd)}} = ``{{oldTotal}}``" -f "New Healing|{{str(constitutionMod*2*%1%)}}" -f "Current HP: | {{min(hp, (constitutionMod*2*%1% - int(oldTotal) + currentHp))}}/{{hp}}{{set_hp(min(hp, (constitutionMod*2*%1% - int(oldTotal)) + currentHp))}}" -color <color>  
```  
  
**Use With:** ``!durable <#dice-under-2xComMod> <#sum-of-dice-under-2xConMod>``