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
!alias tarroka embed {{g,c,v=load_json(get_gvar('ef3e5dd9-17eb-427d-b1af-dee8fa801c23')),min(max(int('%1%'),1),5) if '%1%'!='%1'+'%' else 1, ["first","second","third","fourth","fifth"]}}{{r=roll(f'1d{40 if c<=3 else 14}-1')}}{{d,D='common' if c<=3 else 'high','desc' if c<= 3 else 'descE' if c==4 else 'descS'}}
-title "Madam draws the {{v[c-1]}} card... the {{g[d][r]['name']}}"
-desc "{{g['drawDesc'][c-1]}}

{{g[d][r][D]}}"
-image "{{f"http://i.imgur.com/{g[d][r]['image']}.jpg"}}"
-footer "Tarroka Reading | CoS 11 | !tarroka # - Select which card reading, from 1-5." 
```  
![Alias Preview](https://cdn.discordapp.com/attachments/339575411480592384/392523524041998347/unknown.png)
