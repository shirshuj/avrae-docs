**Updated Toll the Dead**  
*Original alias by Croebh#5603, updated by zhu.exe#4211, updated again by Croebh#5603*  
Uses initiative scripting to determine whether a combatant is injured or not. Use with `!toll` for generic or `!toll [NAME]` in or out of combat to target someone. If in combat, automatically rolls saves and deducts HP.```py  
!alias toll embed {{set("y", 4 if level > 16 else 3 if level > 10 else 2 if level > 4 else 1)}}{{set("z", str(y)+"d8[necrotic]")}}{{set("Z", str(y)+"d12[necrotic]")}}{{c=combat()}}{{tn="&1&" if "&1&" != "&1"+"&" else None}}{{t=c.get_combatant(tn) if c and tn else None}}{{dc=charismaMod+8+proficiencyBonus}}  
-title "<name> casts Toll the Dead{{f' at {t.name}!' if t else (f' at {tn}!' if tn else '!')}}"   
-desc "<name> points at one creature they can see within range (60ft), and the sound of a dolorous bell fills the air around it for a moment. The target must succeed on a **DC {{dc}}** Wisdom saving throw or take {{y}}d8 necrotic damage. If the target is missing any of its hit points, it instead takes {{y}}d12 necrotic damage. "  
{{s=t.save('wis') if t else None}}{{saved=s.total>=dc if s else None}}{{o=(f'-f "Damage|**WIS Save:** {s}; Failure!\n{t.damage(Z).damage}"' if t.ratio < 1 and not saved else (f'-f "Damage|**WIS Save:** {s}; Failure!\n{t.damage(z).damage}"' if not saved else f'-f "Damage|**WIS Save:** {s}; Success!\n**Damage:** `0`"')) if s else None}}  
{{f'-f "Undamaged | {vroll(z)}"\n-f "Damaged | {vroll(Z)}"' if not o else o}}  
{{f'-footer "{t.name}: {t.hp_str()}"' if t else None}}  
```