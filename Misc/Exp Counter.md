**EXP Counter**  
*By Dusk-Argentum#6530 mostly*  
  
Requires: `!cc create EXP`  
```py  
!servalias exp embed -title {{mod_cc("EXP",int("%1%")) if "%1"+"%"!="%1%" else ""}} "<name> {{"gains %1%" if "%1"+"%"!="%1%" else " has "+str(get_cc("EXP"))}} EXP!" {{set("c",get_cc("EXP"))}} -f "Current EXP|{{c}}" -f "Level {{"2" if c<300 else "3" if c<900 else "4" if c<2700 else "5" if c<6500 else "6" if c<14000 else "7" if c<23000 else "8" if c<34000 else "9" if c<48000 else "10" if c<64000 else "11" if c<85000 else "12" if c<100000 else "13" if c<120000 else "14" if c<140000 else "15" if c<165000 else "16" if c<195000 else "17" if c<225000 else "18" if c<265000 else "19" if c<305000 else "20"}} Total|{{"300" if c<300 else "900" if c<900 else "2700" if c<2700 else "6500" if c<6500 else "14000" if c<14000 else "23000" if c<23000 else "34000" if c<34000 else "48000" if c<48000 else "64,000" if c<64000 else "85000" if c<85000 else "100000" if c<100000 else "120000" if c<120000 else "140,000" if c<140000 else "165000" if c<165000 else "195000" if c<195000 else "225000" if c<225000 else "265000" if c<265000 else "305000" if c<305000 else "355000"}}" -color #3d0135 -thumb <image>  
```