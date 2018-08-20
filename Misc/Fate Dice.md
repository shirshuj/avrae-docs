**Fate Dice**  
```GN  
!alias fate_dice_ex embed -title "Fate Dice Example" -desc "4df = {{set('lookup', ' :heavy_plus_sign: \n :heavy_minus_sign: \n :black_large_square: ')}}{{lookup.split('\n')[roll('1d3-1')]}} {{lookup.split('\n')[roll('1d3-1')]}} {{lookup.split('\n')[roll('1d3-1')]}} {{lookup.split('\n')[roll('1d3-1')]}}"```  
   
You can change alias name and title/desc as needed, and/or output format.