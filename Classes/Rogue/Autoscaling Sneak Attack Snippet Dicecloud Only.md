**Autoscaling Sneak Attack Snippet (Dicecloud Only)**  
*By Marcus#3244.*  
If you're using this in initiative, you can remove `[Sneak Attack]` for it to automatically assume the last damage type.  
`!snippet sneak -d "{{ceil(round(max(1, RogueLevel/2) / 2 + max(1, RogueLevel/2) / 2))}}d6[Sneak Attack]"`. Call with `![a|i a <target>] <weapon> sneak [args...]`