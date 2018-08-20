**Deck of Illusions**  
*by @Dominus Croebh*  
  
So, for this one, you need all of the cvars from the pastebins. Then you call it with:  
  
`!deckofillusions`  
  
If you don't want a card in your game, simply rerun the command.  
  
https://pastebin.com/98GazV95  
https://pastebin.com/U5Czvmph  
  
```python  
!alias deckofillusions embed  
{{set('decklist', illusions.split('\n'))}}  
{{set('cardimg', illusionimg.split('\n'))}}  
{{set('num', vroll("1d34").total)}}  
{{set('carddesc',decklist[num])}}  
{{set("img", "https://5etools.com/img/MM/"+str(cardimg[num])+".png")}}  
-title "<name> pulls a card from a Deck of Illusions! - {{carddesc}}"  
-desc "An illusion of a(n) **{{carddesc}}** forms over the thrown card and remains until dispelled. They appear real, of the appropriate size, and behaves as if it were a real creature, except that it can do no harm. While you are within 120 feet of the illusory creature and can see it, you can use an action to move it magically anywhere within 30 feet of its card. Any physical interaction with the illusory creature reveals it to be an illusion, because objects pass through it. Someone who uses an action to visually inspect the creature identifies it as illusory with a successful DC 15 Intelligence (Investigation) check. The creature then appears translucent.  
  
The illusion lasts until its card is moved or the illusion is dispelled. When the illusion ends, the image on its card disappears, and that card can't be used again."  
-thumb "{{img}}"  
```