# Wrath of the Storm
*By ArtLinkov.*

# Usage
Usage is simple, with no requirements: `!wots <target>` or `!wots <target> t` (for thunder damage)

Using it will automatically set up a custom counter called `Wrath of the Strom', 
which resets on long rest and updates the uses/day based on the current WisdomMod.

Other cool features:
1) You can choose Lightning or Thunder damage, which are subject to target's vulnerabilities / ressistances
2) In addition to the save and damage calculation, it sends the DM a private message,
same as a regular spell/attack.
3) If a target is not given, the spell will not waste a counter point.
4) If there are no more uses for that day, the spell will not trigger.
5) Fancy thumbnail.

### Code
```
!alias wots multiline
{{tname="&1&" if "&*&" else ""}}
{{dtype="thunder" if ("&2&"=="thunder" or "&2&"=="t") else "lightning"}}
{{create_cc_nx("Wrath of the Storm", 0, wisdomMod, "long", "bubble")}}
{{max_w=get_cc_max("Wrath of the Storm")}}
{{wp=get_cc("Wrath of the Storm")}}
{{delete_cc("Wrath of the Storm") if max_w!=wisdomMod else ""}}
{{create_cc_nx("Wrath of the Storm", 0, wisdomMod, "long", "bubble") if max_w!=wisdomMod else ""}}
{{set_cc("Wrath of the Storm", wp) if max_w!=wisdomMod else ""}}
{{dc=8+wisdomMod+proficiencyBonus}}
{{c=combat()}}
{{t=c.get_combatant(tname) if tname else None}}
{{s=t.save('dex') if (t!=None and wp>0) else ""}}
{{half=(True if s.total>=dc else False) if s else ""}}
{{save=("(Success!) |"+str(s) if half==True else "(Faliure!) |"+str(s)) if s else "| No target"}}
{{effective_dmg=("2d8/2" if half==True else "2d8") if s else ""}}
{{dmg=t.damage(effective_dmg + "[" + dtype + "]") if s else "" }}
{{mod_cc("Wrath of the Storm",-1) if s else ""}}
!embed    -title "<name> counter-attacks **{{t.name if s else "[No target]"}}** with Wrath of the Storm!"   -f "{{"**Failure!**|Nothing happened, can't cast Wrath of the Storm until a long rest has been completed." if wp<1 else "DEX Save "+save}}" str(dmg.total))}}   -f "{{"" if wp<1 else "DC|"+str(dc)}}"   -f "{{"" if wp<1 else ("Effect|" + dmg.damage + " >> **" + t.name + ":** " + t.hp_str() if s else "")}}"    -f "Remaining Uses | {{cc_str("Wrath of the Storm")}}"    -f "Description| When a creature within 5 feet of you that you can see hits you with an attack, you can use your reaction to cause the creature to make a Dexterity saving throw. The creature takes 2d8 lightning or thunder damage (your choice) on a failed saving throw, and half as much damage on a successful one." -f "Usage| **!wots [target]** (Lightning), or **!wots [target] t** (Thunder)"    -thumb "https://i.imgur.com/Sa1XAtc.png"    -color <color>
!i status {{tname if s else ""}} private
```
