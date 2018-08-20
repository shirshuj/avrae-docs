**Potions of Healing**  
*By Toothless#7854*  
  
Another version of potions of healing. Usage is ``!ipoh <num>``, such as ``!ipoh 8`` where ``<num>`` is the number of d4s rolled. The alias assumes the potion is ``<num>d4 + <num>``. If ``<num>`` is ``4, 8, or 16``, it labels it ``Greater, Superior, and Supreme`` sequentially. Otherwise it is simply ``Potion of Healing``.  
  
To set your color, type ``!cvar color <hex>``, replacing ``<hex>`` with a hex code.  
  
```py  
!alias potion embed   
{{set("name", "Greater" if %1% == 4 else "Superior" if %1% == 8 else "Supreme" if %1% == 16 else "")}}   
{{set("roll", "%1%d4 + %1%")}}   
{{set("heal", vroll(roll))}}   
{{set_hp(min(hp, heal.total + currentHp))}}   
-title "<name> drinks a Potion of {{name}} Healing!"   
-desc "A character who drinks the magical red fluid in this vial regains {{roll}} hit points. Administering or drinking a potion takes an action."   
-f "Healing Recieved|{{str(heal)}}"   
-f "Hit Points|{{get_hp()}} / {{hp}}"   
-footer "Treasure | DMG 187 - 188"   
-color <color>  
```