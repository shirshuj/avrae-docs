**Hit Dice alias, with the Short Rest baggage cut out!**  
  
Use with: `!hd XdY`  
  
```  
!alias hd multiline  
!embed {{set("ds"," (%2%)" if "%2%" in "d4d6d8d10d12d20" else "")}}{{set("ds"," (d"+"%1%".split("d")[1]+")" if "d" in "%1%" else ds)}}{{set("counter", "Hit Dice"+ds)}}{{set("du", 0 if "%1%" == "%1"+"%" or not cc_exists(counter) else int("%1%".split("d")[0]) if "d" in "%1%" else int("%1%"))}}{{set("du",min(get_cc(counter),du) if cc_exists(counter) else 0)}}{{mod_cc(counter, -du, True) if cc_exists(counter) else ""}}{{set("roll",(str(du)+str(hd if exists("hd") and ds=="" else ds[2:-1]))+"+"+str(du*constitutionMod))}}{{set("vheal", vroll("0") if du == 0 else vroll(roll))}}{{set("heal", vheal.total)}}{{set_hp(min(hp, heal + currentHp))}}{{set_hp(min(hp, heal+ currentHp))}} -title "<name> spends {{du}}{{"" if ds=="" else " "+ds[2:-1]}} hit die and recovers {{heal}} hit points." -f "Healing Recieved|{{str(vheal)}}" -f "Current HP: | {{min(hp, (heal + currentHp))}}/{{hp}}{{set_hp(min(hp, (heal + currentHp)))}}" {{"-f \""+counter+" | "+str(get_cc(counter))+"/"+str(get_cc_max(counter))+" "+(str(hd) if ds=="" else "")+"\"" if cc_exists(counter) else ""}} -color <color> -footer "Adventuring | PHB 186"  
```