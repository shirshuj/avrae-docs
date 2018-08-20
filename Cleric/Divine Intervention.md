**Divine Intervention**  
*By Croebh#5603*  
  
This is for the Cleric class feature, Divine Intervention. If you're not using Dicecloud, replace `ClericLevel` with level. As there are two different resets for the feature, you have to manually reset the custom counter, using the `!resetintervention` alias. Obviously, change information around to suit your character.  
  
`!cc create "Divine Intervention" -reset none -max 1 -min 0 -type bubble`  
  
`!alias resetintervention echo {{mod_cc("Divine Intervention",+1)}} "Divine Intervention Reset"`  
  
```py  
!alias intervention embed   
{{set("x", "Divine Intervention")}}  
{{set("y", vroll("1d100"))}}   
{{set("z", ("true" if y.total <= (ClericLevel - 1) else "false"))}}  
-title "<name> {{"attempts to call" if get_cc(x)==0 else "calls"}} on Kelemvor's Aid"  
-desc "He prays to Kelemvor, Judge of the Damned.   
{{"Nothing seems to happen, however. Perhaps they need to wait longer before trying again?" if get_cc(x)==0 else "His prayers are answered. The DM chooses the nature of the intervention." if z == "true" else "His prayers fall on deaf ears, perhaps another day"}}"   
{{"" if get_cc(x)==0 else mod_cc(x, -1)}}  
-f "Divine Intervention | {{"~~" if z == "false" else ""}}{{y}} <= {{ClericLevel}} = {{z}}{{"~~" if z == "false" else ""}}"```