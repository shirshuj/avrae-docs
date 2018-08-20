**Weighted Roll Tables**  
*By Toothless#7854*  
  
Weighted roll tables are tables that have different probabilities for different results. Some results are more common while others are more rare. This snippet of code allows you to create weighed roll tables.  
  
To create a table, type ``!gvar create``, then the table in the following format. Replace ``$gvar$`` in the snippet of code.  
```md  
* Line 1: dieSize, such as "8" for 1d8  
* Each additional line represents a result on the die. For instance, the first line after the dieSize would be the result if the die rolled a 1. The line after that would be the result of the die rolled a 2, etc.  
* For a result, put "#|" followed by the text.  
* For a weighed result, put a "#|". Then, for each line that the die is weighed toward, put a "|".  
```  
**Example:**  
The die rolled is a d8. The first result is weighed 1 - 5, while the next results only occur on a 6, 7, or 8.  
```py  
8  
#|One parent was an elf and the other was a human.  
|  
|  
|  
|  
#|One parent was an elf and the other was a half-elf.  
#|One parent was a human and the other was a half-elf.  
#|Both parents were half-elves.  
```GN  
```py  
{{set("gvar", get_gvar("$gvar$"))}}  
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
{{set("result", lstTxtR[index])}}  
```  
To call the roll, type ``{{roll}}``. To call the result, type ``{{result}}``.