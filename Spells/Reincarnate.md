**Reincarnate**  
*By Toothless#7854*  
  
Rolls for the *reincarnate* spell. An example of the Weighed Roll Table above.  
  
```py  
!alias reincarnate embed   
{{set("gvar", get_gvar("d2ec060d-afce-4fa1-b4f9-76020d89a568"))}}  
{{set("gvarRpl", gvar.replace("\n", "|"))}}  
{{set("lstAll", gvarRpl.split("|"))}}  
{{set("dieSize", lstAll.pop(0))}}  
{{set("lstSym", lstAll[::2])}}  
{{set("lstSymR", lstSym[::-1])}}  
{{set("lstTxt", lstAll[1::2])}}  
{{set("lstTxtR", lstTxt[::-1])}}  
{{set("roll", vroll("1d" + dieSize))}}  
{{set("rTotal", roll.total)}}  
{{set("start", int(dieSize)-rTotal-(rTotal != int(dieSize)))}}  
{{set("index", lstSymR[start:].index("#") + start)}}  
-f "Form | {{"\n" + str(roll) + "\n" + lstTxtR[index]}}"  
```