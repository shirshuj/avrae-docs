**Full Wild Magic Surge**  
*By @Brinjal#4037.*  
I have made my surge command now list the surge  
~~But there's an extra step.  
Go to http://avrae.io/ and to the dashboard, then customisations  
Scroll down to where the cvars are stored and find your WMS (or another character)   
Add a cvar called `st` and for the value paste in the contents of this: https://pastebin.com/3AThUmGV~~ This step is no longer needed after the introduction of global variables!  
Once you've done that, you can roll your surges with:  
```  
!alias surge embed -title "Wild Magic Surge!" -desc "Rolling for wild magic surge.  
  
{{set("st",(get_gvar("87228cfb-43b6-4cd4-ac2e-14b59db149c0").split("|")))}}{{set("roll",vroll("1d20"))}}{{set("r",vroll("1d100"))}}{{set("n",ceil(r.total/2)-1)}}{{str(roll)+"\n\nNo wild magic surge!" if roll.total > 1 else str(roll)+"\n\n**Wild magic surge:** "+str(r)+"\n" + st[n-1]}}"```  
"But brinjal!" you might say: "What if I used tides of chaos. I don't want to have to reroll 50 times until that gets a 1!" No worries, got you covered.  
```  
!alias tides embed -title "Wild Magic Surge!" -desc "  
{{set("st",(get_gvar("87228cfb-43b6-4cd4-ac2e-14b59db149c0").split("|")))}}{{set("n",roll("1d50"))}}{{str((n*2)-roll("1d2-1"))+": "}}{{st[n-1]}}"```  
And, since it's rather easy to do now that the main part of the code is written, here's a function that lets you search for what a number will result in on the table by doing `!searchsurge <NUMBER>`  
```  
!alias searchsurge embed -title "Wild Magic Surge!" -desc "  
{{set("st",(get_gvar("87228cfb-43b6-4cd4-ac2e-14b59db149c0").split("|")))}}{{set("n",ceil(%1%/2))}}{{str(%1%)+": "}}{{st[n-1]}}"```