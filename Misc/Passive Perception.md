**Passive Perception**  
*By silverbass#2407*  
  
Use with `!pp`. You can add `adv` and `dis` to impose +/-5 to the result.   
```  
!alias pp embed {{set("args","%1%%2%%3%%4%%5%%6%%7%%8%%9%")}}{{set("adv", "adv" in args and not "dis" in args)}}{{set("dis", "dis" in args and not "adv" in args)}}{{set("mod",get_raw()["skills"]["perception"])}}{{set("r",vroll("10+"+str(mod)+("+5 [advantage]" if adv else "-5 [disadvantage]" if dis else "")))}} -title "<name> uses their Passive Perception!" -desc "{{r}}" -color <color> -thumb <image>  
```