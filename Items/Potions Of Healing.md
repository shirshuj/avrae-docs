**Potions of Healing**  
*By Toothless#7854*

*Update By nadizak#5061*
  
Another version of potions of healing. Usage is ``!ipoh <num>``, such as ``!ipoh 8`` where ``<num>`` is the number of d4s rolled. The alias assumes the potion is ``<num>d4 + <num>``. If ``<num>`` is ``4, 8, or 16``, it labels it ``Greater, Superior, and Supreme`` sequentially. Otherwise it is simply ``Potion of Healing``.  
  
To set your color, type ``!cvar color <hex>``, replacing ``<hex>`` with a hex code.  
  
```py
!alias potion embed
{{arg = "%1%".lower()}}
{{num = int(''.join([x for x in "0"+arg if x.isdigit()]))}}
{{name = "Greater" if num == 4 or 'gr' in arg else "Superior" if num == 8 or 'supe' in arg else "Supreme" if num == 10 or 'supr' in arg else ""}}
{{rollStr = "10d4+20" if name == "Supreme" else "8d4+8" if name == "Superior" else "4d4+4" if name == "Greater" else "2d4+2"}}
{{heal = vroll(rollStr)}}
{{set_hp(min(hp, heal.total + currentHp))}}
-title "<name> drinks a Potion of {{name}} Healing!"
-desc "A character who drinks the magical red fluid in this vial regains {{rollStr}} hit points. Administering or drinking a potion takes an action."
-f "Healing Recieved|{{heal}}"
-f "Hit Points|{{get_hp()}} / {{hp}}"
-footer "Treasure | DMG 187 - 188"
-color <color>
```
