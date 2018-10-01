**Step of the Wind**

Uses the ability and subtracts Ki Points.

```
!alias windstep embed
{{lvl=int(MonkLevel)}}
{{counter="Ki Points"}}
{{mod_cc(counter, -1)}}
-title "<name> Moves With Ludicrous Speed!"
-desc "You can spend 1 ki point to take the Disengage or Dash action as a bonus action on your turn, and your jump distance is doubled for the turn."
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
-footer "Monk | PHB 78" -color <color> -thumb <image>
```
