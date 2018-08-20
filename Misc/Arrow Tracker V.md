**Arrow Tracker v. 2.0!**  
By Dusk-Argentum#6530   
Now with fixes and improvements!  
  
Tracks how many arrows you used in battles and restores half when run.  
  
  
Add these CC's:  
```  
!multiline !cc create Arrows  
!cc create "Used Arrows"  
```  
*Be sure to set your arrow count correctly via the CC! Just do `!cc Arrows [amount you have]`.*  
*The CC's are cAsE-sEnSiTiVe! If you use a lowercase instead of an uppercase where required, it won't work!*  
*Be sure to surround "Used Arrows" in QUOTES when creating! Otherwise, you will create a CC named "Used"!*  
  
Add this snippet:  
```  
!snippet arrow {{mod_cc("Arrows", -1)}} {{mod_cc("Used Arrows", +1)}} -f "Arrows Remaining|{{get_cc("Arrows")}}" -f "Arrows Used|{{get_cc("Used Arrows")}}"  
```  
  
Then, add this alias:  
```  
!alias arrows embed -color <color> -thumb <image> {{set("usedarrows", get_cc("Used Arrows"))}} {{set("recoveredarrows",usedarrows/2)}} -title "<name> goes to recover their arrows after the battle..." -f "Used Arrows|{{usedarrows}}" -f "Recovered Arrows|{{int(recoveredarrows)}}" {{mod_cc("Arrows",+int(recoveredarrows))}} -footer "Remaining Arrows: {{get_cc("Arrows")}}." {{set_cc("Used Arrows", 0)}}  
```  
  
When you attack with your bow, do `!i a [enemy] [bow name] arrow`. This adds 1 to your `Used Arrows` counter and shows you how many you have left. After combat concludes, simply do `!arrows` and you will retrieve half your arrows. *Doing `!arrows` will reset your "Used Arrows" counter*, which is useful sometimes, but if you do it by mistake, you're on your own.