**Ki Points**

Alias to expend and recharge Ki points.
Works like `!g hp`

```
!alias ki embed
{{lvl=int(MonkLevel)}}
{{counter="Ki Points"}}
{{mod=int("%1%") if "%1"+"%"!="%1%" else 0}}
{{nosign="+" not in "&*&" and "-" not in "&*&"}}
{{mod_cc(counter, mod * (-1 if nosign else 1), True) if "+" not in "&*&" else 0}}
{{mod_cc(counter, mod) if "+" in "&*&" else 0}}
-title "<name> Expends Their Ki!"
-desc "Starting at 2nd level, your access to the mystic energy Ki is represented by a number of ki points. Your monk level determines the number of points you have, as shown in the Ki Points column of the Monk table.

You can spend these points to fuel various ki features. You start knowing three such features: Flurry of Blows, Patient Defense, and Step of the Wind, You learn more ki features as you gain levels in this class,

When you spend a ki point. it is unavailable until you finish a short or long rest, at the end of which you draw all of your expended ki back into yourself. You must spend at least 30 minutes of the rest meditating to regain your ki points."
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
-footer "Monk | PHB 78" -color <color> -thumb <image>
```
