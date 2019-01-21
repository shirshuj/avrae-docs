**Shell Defense**  
*By Croebh#5603 / Marcus#3244 *  
  
An alias for the Tortles racial feature Shell Defense. Adds an effect that adds the AC Bonus.
  
```!alias turtle embed {{c=combat()}}
-title "<name> withdraws into their shell!" -desc "Until they emerge, they gain a +4 bonus to AC, have advantage on Strength and Constitution saving throws. While in their shell, they are prone, speed of 0, with disadvantage on Dexterity saving throws, and cannot take reactions." -f "Armor Class | {{c.me.ac+4 if c else armor+4}} **(+4)**" -f "Speed | 0 speed, Prone, no reactions" -f "Advantage | Strength, Constitution" -f "Disadvantage | Dexterity" -thumb <image>  {{c.me.add_effect('Turtle Shell','-ac +4') if c else ''}}```  
