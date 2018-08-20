**Dawn Alias for Recharging Magic Items!**  
*By silverbass#2407 and Richard P.#0666*   
  
You can add *every single magic item* on your server, and since it checks whether or not you have the right CC's, *anyone from your server can use it.* Just change the names and charge roll dice!  
  
```py  
!servalias dawn embed  
-title "Dawn Breaks over this Cursed Land."   
-desc "Certain magic items regain their charges."  
{{set("r",roll("1d6+1"))}}{{set("counter", "Wand of Magic")}} {{"-f \""+counter+" (+"+str(r)+")|"+("" if mod_cc(counter,r) else "")+'◉'*get_cc(counter)+'〇'*(get_cc_max(counter)-get_cc(counter))+"\"" if cc_exists(counter) else ""}}  
{{set("r",roll("1d6+1"))}}{{set("counter", "Wand of Fireballs")}} {{"-f \""+counter+" (+"+str(r)+")|"+("" if mod_cc(counter,r) else "")+'◉'*get_cc(counter)+'〇'*(get_cc_max(counter)-get_cc(counter))+"\"" if cc_exists(counter) else ""}}  
{{set("r",roll("1d6+1"))}}{{set("counter", "Wand of Detect Magic")}} {{"-f \""+counter+" (+"+str(r)+")|"+("" if mod_cc(counter,r) else "")+'◉'*get_cc(counter)+'〇'*(get_cc_max(counter)-get_cc(counter))+"\"" if cc_exists(counter) else ""}}  
-color <color>  
```