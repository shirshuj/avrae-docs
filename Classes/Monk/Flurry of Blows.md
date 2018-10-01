**Flurry of Blows**

Uses the ability and subtracts Ki Points.

```
!alias flurry embed
{{lvl=int(MonkLevel)}}
{{counter="Ki Points"}}
{{mod_cc(counter, -1)}}
-title "<name> Unleashes a Flurry of Blows!"
-desc "Immediately after you take the Attack action on your turn, you can spend 1 ki point to make two unarmed strikes as a bonus action."
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
-footer "Monk | PHB 78" -color <color> -thumb <image>
```
