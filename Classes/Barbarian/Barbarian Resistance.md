**Barbarian Resistance**  
To add a barbarian character's damage resistances when they enter a Rage you can use the command:  
  
 `!init opt [character name] -resist bludgeoning -resist slashing -resist piercing`  
  
 If you are a Bear Totem Barbarian use:   
  
` !alias BearRage init opt <name> -resist bludgeoning -resist slashing -resist piercing -resist acid -resist cold -resist fire -resist force -resist lightning -resist necrotic -resist poison -resist radiant -resist thunder`  
  
To make this even faster you can create an alias for the command using:   
  
`!alias ragesist(or whatever else you want to name it) init opt [character name] -resist bludgeoning -resist slashing -resist piercing`   
  
You can then just use the command `!ragesist` when you activate rage..  
  
Whether you use the base command or create an alias you will need to run it in every new combat.