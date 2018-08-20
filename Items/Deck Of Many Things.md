**Deck of Many Things**  
*by @Dominus Croebh*  
  
So, for this one, you need all of the cvars from the pastebins. Then you call it with:  
  
`!deckofmany [#]`  
  
The deck maxes at 22. You might notice the images don't match the names, I'm too lazy to photoshop new images.  
Cards with a 👑 are only available in the full deck, as per DMG.162.  
  
If you don't want a card in your game, simply rerun the command.  
  
https://pastebin.com/g1FJ7VVe  
https://pastebin.com/Tdzi6hbK  
https://pastebin.com/iA3WXACa  
https://pastebin.com/E2rCFdPj  
  
```python  
!alias deckofmany embed  
{{set('totaldeck',deckofmany1+"\n"+deckofmany2+"\n"+deckofmany3)}}  
{{set('decklist', totaldeck.split('\n'))}}  
{{set('cardimg', deckofmanyimg.split('\n'))}}   
{{set('num', vroll("1d"+str(min(22,%1%))).total)}}  
{{set('carddesc',decklist[num*2])}}  
{{set('cardname',decklist[(num*2)-1])}}  
{{set("img", "http://i.imgur.com/"+str(cardimg[num])+".jpg")}}  
-title "<name> pulls a card from a Deck of Many Things - {{cardname}}!"  
-desc "{{carddesc}}"  
-image "{{img}}"  
```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/392573284396564480/unknown.png)