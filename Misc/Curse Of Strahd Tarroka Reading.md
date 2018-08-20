**Curse of Strahd Tarroka Reading**  
*by Croebh#5603*  
  
Hokay, so this ones a bit of a doozy. Will do each of the 5 Tarroka card readings for the Curse of Strahd campaign. Refer to page 11 of the Curse of Strahd book in order to decifer this for your players. Displays an image of the card as well.  
  
`!tarroka [card #]`  
  
`!tarroka 1` for The Tome of Strahd  
`!tarroka 2` for The Holy Symbol of Ravenkind  
`!tarroka 3` for The Sunsword  
`!tarroka 4` for Strahd's Enemy  
`!tarroka 5` for Strahd  
```python  
!alias tarroka embed   
{{set('c',int('%1%') if '%1%'!='%1'+'%' else 1)}}  
{{set('cardimg', get_gvar('8f1d64f3-4dfa-4704-a72c-66608f414b0c').split('\n'))}}   
{{set('tarrotread', get_gvar('259d318b-6de4-4642-8102-5e963437a2db').split('\n'))}}   
{{set('tarrotname', get_gvar('d1371695-5691-4185-9f09-14ed9ddad782').split('\n'))}}   
{{set("verbose","first" if c == 1 else "second" if c == 2 else "third" if c == 3 else "fourth" if c == 4 else "fifth")}}  
{{set("card",vroll("1d40").total if c <= 3 else vroll("1d14").total)}}  
{{set("namenum",card if c <= 3 else card+40)}}  
{{set("descnum",card if c <= 3 else card+40 if c == 4 else card+54)}}  
{{set("img", "http://i.imgur.com/"+str(cardimg[card])+".jpg" if c <= 3 else "http://i.imgur.com/"+str(cardimg[card+40])+".jpg")}}  
{{set("descvar",get_gvar('d48590b0-0739-4ca7-a00c-cffc49f851f6'))}}  
{{set("carddesc", descvar.split('\n'))}}  
-title "Madam draws the {{verbose}} card... the {{tarrotname[namenum]}}"  
-desc "{{tarrotread[c]}}  
  
{{carddesc[descnum]}}"  
-image "{{img}}"  
```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/392523524041998347/unknown.png)