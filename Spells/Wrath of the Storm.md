# Wrath of the Storm
*By ArtLinkov.*

# Usage
Usage is simple, with no requirements: `!wots <target>`

Using it will automatically set up a custom counter called `Wrath of the Strom', 
which resets on long rest and updates the uses/day based on the current WisomMod.

Other cool features:
1) In addition to the save and damage calculation, it sends the DM a private message,
same as a regular spell/attack.
2) If a target is not given, the spell will not waste a counter point.
3) If there are no more uses for that day, the spell will not trigger.
4) Fancy thumbmail.

### Code
```
!alias wots multiline {{tname="&*&" if "&*&" else ""}}
!embed   {{create_cc_nx("Wrath of the Storm", 0, wisdomMod, "long", "bubble")}}   {{max_w=get_cc_max("Wrath of the Storm")}}   {{wp=get_cc("Wrath of the Storm")}}   {{delete_cc("Wrath of the Storm") if max_w!=wisdomMod else ""}}   {{create_cc_nx("Wrath of the Storm", 0, wisdomMod, "long", "bubble") if max_w!=wisdomMod else ""}}   {{set_cc("Wrath of the Storm", wp) if max_w!=wisdomMod else ""}}   {{dc=8+wisdomMod+proficiencyBonus}}   {{c=combat()}}   {{t=c.get_combatant(tname) if tname !="" else ""}}   {{s=t.save('dex') if t else ""}}   {{half=(True if s.total>=dc else False) if t else ""}}   {{dmg=vroll("2d8")}}   {{save=("(Success!) |"+str(s) if half==True else "(Faliure!) |"+str(s)) if s else "| No target"}}   -title "<name> counter-attacks **{{t.name if t !="" else "[No target]"}}** with Wrath of the Storm!"   -thumb "https://i.imgur.com/tfx2tsE.png"   -f "{{"**Failure!**|Nothing happened, can't cast Wrath of the Storm until a long rest has been completed." if wp<1 else "**DEX Save** "+save}}"   {{dmg_str=dmg.dice+"= **"+((str(floor(dmg.total/2))+"** (halved)" if half==True else str(dmg.total)+"**") if t else str(dmg.total)+"**")}}   -f "{{"" if wp<1 else "**Damage** | "+dmg_str}}"   {{effective_dmg=(floor(dmg.total/2) if half==True else dmg.total) if s else 0}}   {{t.mod_hp(-effective_dmg) if t and wp>0 else ""}}   {{mod_cc("Wrath of the Storm",-1) if t and wp>0 else ""}}   -f "Status| {{(t.name + ": " + t.hp_str()) if t else "No target"}}"   -f "Remaining Wrath of the Strom | {{cc_str("Wrath of the Storm")}}"   -f "Effect| When a creature within 5 feet of you that you can see hits you with an attack, you can use your reaction to cause the creature to make a Dexterity saving throw. The creature takes 2d8 lightning or thunder damage (your choice) on a failed saving throw, and half as much damage on a successful one." -color <color>
!i status {{tname if tname else ""}} private
```
