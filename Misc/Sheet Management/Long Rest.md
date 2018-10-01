**Long Rest**  
*By too many people now*  
```py  
!alias lr g {{set("n",max(1,level/2))}}  
{{set("counter","Hit Dice (d20)")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
{{set("counter","Hit Dice (d12)")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
{{set("counter","Hit Dice (d10)")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
{{set("counter","Hit Dice (d8)")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
{{set("counter","Hit Dice (d6)")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
{{set("counter","Hit Dice (d4)")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
{{set("counter","Hit Dice")}}{{"" if not cc_exists(counter) else set_cc(counter,min(get_cc_max(counter),get_cc(counter)+min(n,get_cc_max(counter))))}}{{"" if not cc_exists(counter) else set("n",n-min(n,get_cc_max(counter)))}}  
lr  
```