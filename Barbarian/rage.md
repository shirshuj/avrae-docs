# Rage
*By Theodore#7790.*

Subtracts 1 from `Rage` counter and applies resistance along with Rage damage.  
Can only be used while in initiative. 

### Usage
`!rage`

### Setup
`!cc create Rage -min 0 -max # -type bubble -reset long`  
Insert your number of times you can rage per long rest instead of #

### End Early
`!i re "<name>" Rage`  
`!i opt "<name>" -resist bludgeoning -resist slashing -resist piercing`

### Code
```GN
!alias rage multiline
!embed {{c,cc,lvl,target,b=combat(),"Rages" if cc_exists("Rages") else "Rage",int(BarbarianLevel) if exists("BarbarianLevel") else level,"&*&" if "&*&" else name,['bludgeoning','piercing','slashing']}} {{v=cc_exists(cc) and get_cc(cc)>0}} -title "{{f'{target.title()} {"Rages" if v else "tries to Rage"}!'}}" -desc "{{"You have advantage on Strength checks and Strength saving throws, and are unable to cast or concentrate on spells. Your rage ends early if you are knocked unconscious or if your turn ends and you haven't attacked a hostile creature since your last turn or taken damage since then, or as a bonus action on your turn." if v else "You must finish a long rest before you can use this ability again." if cc_exists(cc) else "You do not have this ability"}}" {{mod_cc(cc,-1) if v and level<20 else ""}} -f "Rages | {{(cc_str(cc) if lvl<20 else "Unlimited") if cc_exists(cc) else "*None*"}}" -footer "Barbarian | PHB 48" -color <color> {{mod_cc("Fanatical Focus",1) if cc_exists("Fanatical Focus") else ""}}{{"-f 'Fanatical Focus|"+cc_str("Fanatical Focus")+"'" if cc_exists("Fanatical Focus") else ""}}{{t=c.get_combatant(target).resists.resist if c and c.get_combatant(target).resists else ""}}{{T=["-resist "+x for x in b if x not in t]}}
{{'!i effect "'+target+'" Rage -dur 10 -d '+str(2 if lvl<9 else 3 if lvl<16 else 4) if v and c else ""}}
{{'!i opt "'+target+'" '+' '.join(T) if v and c and T else ""}}```
