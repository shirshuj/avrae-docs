**Jumping Rules**

Prints out the rules for jumping and calculates your jumping distances.
Doesn't account for class features or items but gives you a base number.
You can add long or high to the call to print only the rule for that jump.

```
!alias jump embed
{{long='l' in "&*&"}}
{{high='h' in "&*&"}}
{{both=('%1%' == '%1'+'%')}}
-title "Jumping Rules!"
-desc "Your Strength determines how far you can jump.
{{'''\n**Long Jump**. When you make a long jump, you cover a number of feet up to your Strength score if you move at least 10 feet on foot immediately before the jump. When you make a standing long jump, you can leap only half that distance. Either way, each foot you clear on the jump costs a foot of movement.\n\nThis rule assumes that the height of your jump doesn’t matter, such as a jump across a stream or chasm. At your DM’s option, you must succeed on a DC 10 Strength (Athletics) check to clear a low obstacle(no taller than a quarter of the jump’s distance), such as a hedge or low wall. Otherwise, you hit it.\n\nWhen you land in difficult terrain, you must succeed on a DC 10 Dexterity (Acrobatics) check to land on your feet. Otherwise, you land prone.''' if (both or long) else ''}}
{{'''**High Jump**. When you make a high jump, you leap into the air a number of feet equal to 3 + your Strength modifier if you move at least 10 feet on foot immediately before the jump. When you make a standing high jump, you can jump only half that distance. Either way, each foot you clear on the jump costs a foot of movement. In some circumstances, your DM might allow you to make a Strength (Athletics) check to jump higher than you normally can.\n\nYou can extend your arms half your height above yourself during the jump. Thus, you can reach above you a distance equal to the height of the jump plus 1 1/2times your height.''' if (both or high) else ''}}"
{{f'-f "**Long Jump** (Standing)| {strength} feet ({strength/2} feet)"' if (both or long) else ''}}
{{f'-f "**High Jump** (Standing)| {3+strength} feet ({(3+strength)/2} feet)"' if (both or high) else ''}}
```
