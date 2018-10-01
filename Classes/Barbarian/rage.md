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
`!i effect "<name>" 10 "Rage" -d "{{floor(level/9)+floor(level/16)-floor(level/18)+2}}"`  
`!i opt "<name>" -resist bludgeoning -resist slashing -resist piercing`

### Code
```GN
!alias rage multiline
!embed  {{set("counter", "Rage")}}{{set("v",get_cc(counter) > 0)}} -title "<name> {{"Rages" if v else "tries to Rage"}}!" -desc "{{"You have advantage on Strength checks and Strength saving throws, and are unable to cast or concentrate on spells. Your rage ends early if you are knocked unconscious or if your turn ends and you haven't attacked a hostile creature since your last turn or taken damage since then, or as a bonus action on your turn." if v else "You must finish a long rest before you can use this feature again."}}" {{mod_cc(counter, -1) if level < 20 and v else ""}} -f "Rage | {{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter)) if level < 20 else "Unlimited"}}" -footer "Barbarian | PHB 48" -color <color>
!i effect "<name>" 10 "Rage" -d "{{floor(level/9)+floor(level/16)-floor(level/18)+2}}"
!i opt "<name>" -resist bludgeoning -resist slashing -resist piercing```
