**Wand of Wonder**  
*By Toothless#7854, courtesy of Egon#1300*  
  
Creates "Wand of Wonder" counter if nonexistent. Subtracts 1 from "Wand of Wonder" counter. Rolls on *wand of wonder* table and displays roll and result.  
  
Uses Weighted Tables alias.  
  
```py  
!alias wonder embed  
{{set("gvar", get_gvar("1c46d556-dfef-4d5b-99f9-cb94655b36b6"))}}  
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
{{set("counter", "Wand of Wonder")}}  
{{create_cc_nx(counter, 0, 7, "none", "bubble")}}  
{{mod_cc(counter, -1)}}  
-title "<name> uses Wand of Wonder!"  
-desc "This wand has 7 charges. While holding it, you can use an action to expend 1 of its charges and choose a target within 120 feet of you. The target can be a creature, an object, or a point in space."  
-f "Roll | {{roll}}"  
-f "Effect | {{result}}"  
-f "{{counter}} | {{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"  
-footer "Treasure | DMG 212 - 213"  
-color <color>   
```