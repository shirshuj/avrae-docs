**Bard Mantle of Inspiration**  
*By Marcus#3244 with lots of wonderful help from silverbass#2407*  
  
Prints a description of Mantle of Inspiration and adds the relevant amount of HP to the specified targets, up to 5, and then removes a use of Bardic Inspiration.  
  
**Usage example:** `!mantle John Mary Kyle Sue Bob`  
  
```python  
!alias mantle multiline  
!embed {{set("counter", "Bardic Inspiration")}} -title "<name> {{"uses" if get_cc(counter)>0 else "tries to use"}} Mantle of Inspiration!" -desc "As a bonus action, you can expend one use of your Bardic Inspiration to grant yourself a wondrous appearance. When you do so, choose a number of creatures you can see and that can see you within 60 feet of you, up to a number equal to your Charisma modifier (minimum of one). Each of them gains 5 temporary hit points. When a creature gains these temporary hit points, it can immediately use its reaction to move up to its speed, without provoking opportunity attacks." {{mod_cc(counter,-1,True) if get_cc(counter)>0 else ""}} -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -footer "Bard | XGtE 14" -color <color> -thumb <image> {{set("a", BardLevel)}}{{set("b", 5 if a<5 else 8 if a<10 else 11 if a<15 else 14)}}{{set("t1","&1&")}}{{set("t2","&2&")}}{{set("t3","&3&")}}{{set("t4","&4&")}}{{set("t5","&5&")}}  
{{"!i hp \""+t1+"\" "+str(b) if t1!="&1"+"&" else ""}}  
{{"!i hp \""+t2+"\" "+str(b) if t2!="&2"+"&" else ""}}  
{{"!i hp \""+t3+"\" "+str(b) if t3!="&3"+"&" else ""}}  
{{"!i hp \""+t4+"\" "+str(b) if t4!="&4"+"&" else ""}}  
{{"!i hp \""+t5+"\" "+str(b) if t5!="&5"+"&" else ""}}```