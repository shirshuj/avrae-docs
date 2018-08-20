**Automatic Bless**  
Since Bless is often forgotten in initiative, this command allows you to run `!bless [character]` to automatically add an effect to them in initiative for 10 rounds, which automatically adds 1d4 to their to-hit rolls. To end it (in case concentration drops), run `!i re [character] Bless`.  
`!alias bless i effect %1% 10 Bless -b 1d4[Bless]`  
^ this format can be edited for other purposes, like Rage damage:  
`!alias rage i effect %1% 10 Rage -d 2[Rage]`