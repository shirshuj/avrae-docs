**Bag of Tricks**  
*By Croebh#5603*  
  
A simple Bag of Tricks alias/cc. This one is set for the Gray version, should be easily adaptable to the other two versions.  
  
Call with `!baggray`  
  
`!cc create "Bag of Tricks, Gray" -max 3 -min 0 -reset long`  
  
```python  
!alias baggray embed {{set('a', vroll('1d8'))}}  
{{set('b', ['Weasel', 'Giant Rat', 'Badger', 'Boar', 'Panther', 'Giant Badger', 'Dire Wolf', 'Giant Elk'])}}  
{{set('c', ['Weasel', 'Giant%20Rat', 'Badger', 'Boar', 'Panther', 'Giant%20Badger', 'Dire%20Wolf', 'Giant%20Elk'])}}  
{{set('z', 'Bag of Tricks, Gray')}}  
{{set('x', "~~" if get_cc(z) == 0 else "")}}  
-title "<name> uses their Bag of Tricks, Gray!"  
-desc "{{x}}They use an action to pull a fuzzy object from the bag, and throw it up to 20 feet. When it landed, it transformed into a **{{b[a.total-1]}}**! This creature vanishes at the next dawn, or when it's reduced to 0 hit points.  
  
The {{b[a.total-1]}} is friendly to you and your companions, and acts on your turn. You can use a bonus action to give it directions. In the abscene of commands, it acts as it would in nature.{{x}}  
  
Once three fuzzy objects have been pulled from the bag, it can't be used until the next dawn."  
-f "Bag of Tricks, Gray |{{x}} {{a.dice}} = {{b[a.total-1]}}{{x}}"  
-f "Fuzzy Objects |{{"" if get_cc(z) == 0 else mod_cc(z, -1)}} {{'◉'*get_cc(z) + '〇'*(get_cc_max(z)-get_cc(z))}}"  
-footer "DMG.154"  
-image "https://cdn.discordapp.com/attachments/269276476023635978/396341937323376642/BiggerGrayBag609-1.png"  
-thumb "https://5etools.com/img/MM/{{c[a.total-1]}}.png"  
```