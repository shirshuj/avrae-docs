**Deflect Missiles**

Rolls for the Deflect Missiles damage reduction. If you run it again and add catch it subtracts a Ki point and prints rule for throwing it.

```
!alias deflect embed
{{lvl=int(MonkLevel)}}
{{counter="Ki Points"}}
{{catch=("%1"+"%" != "%1%")}}
{{mod_cc(counter, -1) if catch else 0}}
{{reduce=vroll(f"1d10+{dexterityMod}+{MonkLevel}")}}
-title "<name> {{"Deflects" if not catch else "Catches"}} the Projectile!"
-desc "Starting at 3rd level, you can use your reaction to deflect or catch the missile when you are hit by a ranged weapon attack. When you do so, the damage you take from the attack is reduced by 1d10 + your Dexterity modifier + your monk level.

If you reduce the damage to 0, you can catch the missile if it is small enough for you to hold in one hand and you have at least one hand free. If you catch a missile in this way, you can spend 1 ki point to make a ranged attack (20/60 feet) with the weapon or piece of ammunition you just caught, as part of the same reaction. You make this attack with proficiency, regardless of your weapon proficiencies, and the missile counts as a monk weapon for the attack."
{{f'-f "Damage Reduction|{reduce}"' if not catch else ''}}
{{f'-f "{counter}|{"◉"*get_cc(counter)}{"〇"*(get_cc_max(counter)-get_cc(counter))}"' if catch else ''}}
-footer "Monk | PHB 78" -color <color> -thumb <image>
```
