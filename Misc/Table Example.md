**Table Example!**  
*By silverbass#2407*  
```  
!alias tabletest embed -title "silverbass's Table Framework" {{g=get_gvar("93e8c703-3090-4d3d-aaa5-bae0a18b010f").split("\n")}}  
{{r=vroll("1d100")}}  
{{lines=[i.split("|") for i in g]}}  
-desc "{{r}}  
{{"".join([line[2] for line in lines if int(line[0])<=r.total<int(line[1])])}}"  
-footer "Gvar Source: 93e8c703-3090-4d3d-aaa5-bae0a18b010f"  
-f "Gvar Text|{{get_gvar("93e8c703-3090-4d3d-aaa5-bae0a18b010f")}}"  
```