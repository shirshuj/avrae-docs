**Alternative Number of Death Saves!**  
*By silverbass#2407, request by newtim#1227*   
  
```py  
!alias ds embed   
{{(create_cc_nx("Failed Death Saves", 0, 5, "none", "bubble") or set_cc("Failed Death Saves",0)) if not cc_exists("Failed Death Saves") else ""}}  
{{(create_cc_nx("Successful Death Saves", 0, 5, "none", "bubble") or set_cc("Successful Death Saves",0)) if not cc_exists("Successful Death Saves") else ""}}  
{{set("f","%1%".lower() in "fail")}}{{set("g","%1%".lower() in "reset")}}  
{{set("b",int("%1%") if not f and not g and "%1"+"%"!="%1%" else 0)}}  
{{set("c","" if b==0 else "+"+str(b) if b>0 else str(b))}}  
{{set("d",int("%2%") if f and not g and "%2"+"%"!="%2%" else 1)}}  
-title "<name> {{"resets Death Saves!" if g else "fails "+("a" if d==1 else str(d))+" Death Save!" if f else "makes a Death Save!"}}"   
{{set("r",vroll("1d20"+c))}}  
{{str(set_cc("Failed Death Saves",0) )+str(set_cc("Successful Death Saves",0)) if r.total-b==20 else (set_cc("Successful Death Saves",0) or set_cc("Failed Death Saves",0)) if g else mod_cc("Failed Death Saves",d) if f else (mod_cc("Failed Death Saves",2) if r.total<2 else mod_cc("Failed Death Saves",1) if r.total<10 else mod_cc("Successful Death Saves",1) if r.total>9 else "")}}  
-desc "{{"" if g else "Added "+str(d)+" failed death save." if f else r}}"   
-f "Death Saves|F {{'〇'*(get_cc_max("Failed Death Saves")-get_cc("Failed Death Saves"))+'◉'*get_cc("Failed Death Saves")}} | {{'◉'*get_cc("Successful Death Saves")+'〇'*(get_cc_max("Successful Death Saves")-get_cc("Successful Death Saves"))}} S"   
{{"-footer \""+name+" is UP with 1 HP!\"" if r.total-b==20 else "" "-footer \""+name+" is DEAD!\"" if get_cc_max("Failed Death Saves")==get_cc("Failed Death Saves") else "-footer \""+name+" is STABLE!\"" if get_cc_max("Successful Death Saves")==get_cc("Successful Death Saves") else ""}}  
-color <color> -thumb <image>  
```  
Literally just download as a server alias and have players use `!ds`. It sets up its own cc's automatically. Change the number `5` to however many saves or failures you desire.