**Empty Body**

Uses the ability and subtracts Ki Points.

```
!alias empty embed
{{lvl=int(MonkLevel)}}
{{counter="Ki Points"}}
{{mod_cc(counter, -4)}}
-title "<name> Focuses and Vanishes from Sight!"
-desc "Beginning at 18th level, you can use your action to spend 4 ki points to become invisible for 1 minute. During that time, you also have resistance to all damage but force damage.

Additionally, you can spend 8 ki points to cast the Astral Projection spell, without needing material components. When you do so, you can't take any other creatures with you."
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
-footer "Monk | PHB 79" -color <color> -thumb <image>
```
