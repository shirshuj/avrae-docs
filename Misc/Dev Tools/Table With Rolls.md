**Table with Rolls**  
*By silverbass#2407*  
  
```  
!alias tabletest2 embed -title "silverbass's Table Framework, v2" {{g=get_gvar("ab4a805e-626b-40d9-be27-b6fa16cc150f").split("\n")}}  
{{r=vroll("1d100")}}  
{{lines=[i.split("|") for i in g]}}  
-desc "{{r}}  
{{"".join([line[2].replace("#1#",str(vroll(line[3]) if line[3] else "")) for line in lines if int(line[0])<=r.total<int(line[1])])}}"  
-footer "Gvar Source: ab4a805e-626b-40d9-be27-b6fa16cc150f"  
-f "Gvar Text|{{get_gvar("ab4a805e-626b-40d9-be27-b6fa16cc150f")}}"  
```