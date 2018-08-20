**Second Wind**  
*By Croebh#5603.*  
Takes max HP into account. The first is for Dicecloud sheets, the second for others.  
```md  
!alias second embed -title "<name> takes a Second Wind" -desc "They pause and take in a deep breath. After a moment you see their wounds begin to stitch themselves shut." -f "Second Wind heals for: | {{set('roll', roll('1d10'))}}1d10 ({{"**"+str(roll)+"**" if roll==10 or roll==1 else roll}}) + {{FighterLevel}} = {{roll+FighterLevel}}{{set('healed', roll + currentHp + FighterLevel)}}." -f "Current HP: | {{min(hp, healed)}}/{{hp}}{{set_hp(min(hp, healed))}}" -thumb <image>  
```GN  
```GN  
!alias second embed -title "<name> takes a Second Wind" -desc "They pause and take in a deep breath. After a moment you see their wounds begin to stitch themselves shut." -f "Second Wind heals for: | {{set('roll', roll('1d10'))}}1d10 ({{"**"+str(roll)+"**" if roll==10 or roll==1 else roll}}) + {{level}} = {{roll+level}}{{set('healed', roll + currentHp + level)}}." -f "Current HP: | {{min(hp, healed)}}/{{hp}}{{set_hp(min(hp, healed))}}" -thumb <image>```