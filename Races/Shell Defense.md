**Shell Defense**  
*By Croebh#5603 / Marcus#3244 *  
  
An couple aliases for the Tortles racial feature Shell Defense. If you don't use the `!init` system, simply remove the last line.   
  
```!alias turtle multiline   
!embed -title "<name> withdraws into their shell!" -desc "Until they emerge, they gain a +4 bonus to AC, have advantage on Strength and Constitution saving throws. While in their shell, they are prone, speed of 0, with disadvantage on Dexterity saving throws, and cannot take reactions." -f "Armor Class | {{armor+4}} **(+4)**" -f "Speed | 0 speed, Prone, no reactions" -f "Advantage | Strength, Constitution" -f "Disadvantage | Dexterity" -thumb <image>  
!i opt <name> -ac {{armor+4}}```  
  
```!alias unshell multiline  
!embed -title "<name> comes back out of their shell!" -f "Armor Class | {{armor}}"  
!i opt <name> -ac {{armor}}```