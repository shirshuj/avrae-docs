**Arcane Shot**  
*By Croebh#5603*  
  
This is an alias to perform Arcane Shots for the Arcane Archer subclass for Fighter. To set it up, you'll need the custom counter. After that, you can call with `!arcaneshot [shot]`.  
  
`!cc create "Arcane Shot" -reset short -max 2 -min 0 -type bubble`  
  
```py  
!alias arcaneshot embed {{set('a',['shadow','piercing','seeking','grasping','banishing','enfeebling','beguiling','bursting','%1%'])}}   
{{set("x", "Arcane Shot")}}  
{{set("shot", "FIZZLE" if get_cc(x)==0 else "Uuuuh" if "%1%" == "%1"+"%" else "Banishing Arrow" if str("%1%")=="banishing" else "Beguiling Arrow" if str("%1%")=="beguiling" else "Bursting Arrow" if str("%1%")=="bursting" else "Enfeebling" if str("%1%")=="enfeebling" else "Grasping Arrow" if str("%1%")=="grasping" else "Piercing Arrow" if str("%1%")=="piercing" else "Seeking Arrow" if str("%1%")=="seeking" else "Shadow Arrow" if str("%1%")=="shadow" else "Uuuuh")}}  
{{set('b',a.index("%1%"))}}  
-title "<name> transforms that last shot into an Arcane Shot: {{shot}}"  
{{set('d',[2,1,1,2,1,2,2,2,3])}}  
{{set('k',str(d[b]*2 if level >= 18 else d[b]))}}  
{{set('D',['psychic','piercing','force','poison','force','necrotic','psychic','force','None'])}}  
{{set('v',"" if b == 4 and level <= 17 else vroll(k+'d6['+D[b]+']'))}}  
{{"-f \'Check/Save DC|"+str(8+proficiencyBonus+intelligenceMod)+"\'" if b < 6 else ""}}          
-f "Damage |{{"Not yet!" if b == 8 or shot=="FIZZLE" else "None until lvl 18." if b == 4 and level <= 17 else str(v)+'on Fail | `'+str(floor(v.total/2))+'`on Success' if b == 1 or b ==2 else v}}"  
{{"" if shot=="Uuuuh" or shot=="FIZZLE" else mod_cc(x, -1)}}  
-f "Arcane Shots | {{get_cc(x)}}/{{get_cc_max(x)}}"  
-desc "{{"Unfortunately, they dont have any charges of Arcane Shot left until they take a rest" if shot=="FIZZLE" else get_gvar('07f63714-bbcd-4200-aa8e-963ed092856f') if shot=="Uuuuh" else get_gvar('405f96dd-ca13-4858-a8ef-4eaa4e91652c').split('\n')[b]}}"  
```  
https://drive.google.com/drive/folders/1EJx9A4Rje-Yj98SKUZNHSr3UXDFPi6qF  
A drive folder with all of the above organized by classes, race and general