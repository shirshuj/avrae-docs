# MIMsy the Mirror Image Manager
*By Derixyleth#0636.*

MIMsy is a *mirror image* manager. MIMsy casts *mirror image* and sets a cvar for you active duplicates. Then, whenever you're attacked, run `!mim check <attack roll> [damage roll]` and MIMsy will check if the attack targeted a duplicate or your character. If the attack targeted a duplicate, it will adjust your HP up by [damage roll]. `!mim` with no args will give you more details.


### Code
```
!alias mim {{s,n="&1&",name}}{{m=1 if s in "cast" else 2 if s in "check" else 3 if s in "drop" else 4}}{{set_cvar("dupes",3) if m==1 else set_cvar("dupes",0) if m==3 else set_cvar_nx("dupes",0)}}{{du,a,d,r=int(dupes),int("&2&") if "&2&".isdigit() else 0,0 if "&" in "&3&" or not "&3&".isdigit() else int("&3&"),vroll("1d20")}}{{RO,DAC=12-du-(du if du>1 else 0),10+dexterityMod}}{{t,DN=(r.total>=RO),[n,"a duplicate"]}}{{h,HM=a>=DAC if t else a>armor,["missed","hit"]}}{{set_hp(min(hp,d+get_hp())) if t and m==2 else ""}}{{mT=get_gvar("269708a7-bee6-4282-9bf8-af22ff0880d5").replace("HM",HM[h]).replace("DN",DN[t]).replace("NU",str(du)).replace("S ","s " if du>1 else " ").replace("RO",str(RO)).replace("DAC",str(DAC)).replace("NA",n).split("~")}}{{nu=max(0,(du-(h and t))) if m==2 else du}}{{mT[0]+('&*&'.replace('&1& ','')) if m==1 else mT[1]+' -f "d20 Roll|'+str(r)+'" -f "Duplicates|'+('◉'*nu + '〇'*(3-nu))+('" -f "'+n+'\'s Adjusted HP|'+str(get_hp())+'/'+str(hp) if t and d else '')+'"' if m==2 and du else mT[2] if m==3 else mT[3] if m==4 else mT[4]}}{{mT[5]}}{{set_cvar("dupes",nu)}} -color <color> -image <thumb>
```
