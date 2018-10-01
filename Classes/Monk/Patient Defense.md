**Patient Defense**

Uses the ability and subtracts Ki Points.

```
!alias patient embed
{{lvl=int(MonkLevel)}}
{{counter="Ki Points"}}
{{mod_cc(counter, -1)}}
-title "<name> Enters a Defensive Stance!"
-desc "You can spend 1 ki point to take the Dodge action as a bonus action on your turn."
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
-footer "Monk | PHB 78" -color <color> -thumb <image>
```
