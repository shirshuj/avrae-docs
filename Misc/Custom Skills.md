**Custom Skills**  
  
An alias to roll skills in a way that mimics standard skill rolls. Useful if you have some sort of custom skill used in your game or want a convenient way to roll tool based checks.  
  
```GN  
!alias [skill/tool name] embed -f "**<name> makes a [Name of the skill/tool] check!**| {{set('roll', roll('1d20'))}}1d20 ({{roll}}) + {intelligenceMod + proficiencyBonus} = {{roll+intelligenceMod+proficiencyBonus}}" -thumb <image>```  
  
Note you may need to change `intelligenceMod` to the ability relevant to your skill/tool check.  
  
Example: