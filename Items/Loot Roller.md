**Loot Roller!**  
*By Boots McStompy#8795 and silverbass#2407*  
  
Pulls loot from DMG and XGtE! Currently set as one of this server's servaliases, so feel free to test it out in <#269276476023635978>   
```py  
!servalias loot multiline  
!embed {{set("rar","%1%".lower() if "%1" + "%" != "%1%" else "common")}}{{set("proper","Common" if rar[0:3] == "com" else "Uncommon" if rar[0:3] == "unc" else "Rare" if rar[0:3] == "rar" else "Very Rare" if rar[0:3] == "ver" else "Legendary" if rar[0:3] == "leg" else "ERROR")}} -title "Rolling for a {{proper}} Magic Item!" {{set("items", get_gvar("d3ae294a-f25d-4487-9300-6883cca339ce").split('\n')[1::] if rar[0:3] == "com" else get_gvar("cf95d38b-ce56-4687-8934-def1490c07b0").split('\n')[1::]+get_gvar("aa8a49a6-c9e0-4d0b-9fb2-fd91fa6c7f76").split('\n')[2::] if rar[0:3] == "unc" else get_gvar("e94e05aa-3ca5-4d64-aaf3-465f72396fa5").split('\n')[1::]+get_gvar("3555fb93-5d2f-46ee-b4ba-f876cae8db61").split('\n')[2::] if rar[0:3] == "rar" else get_gvar("41c18347-e4b1-4d9f-960d-9d8d6b5bf8c9").split('\n')[1::] if rar[0:3] == "ver" else get_gvar("be67dd4d-85c2-4078-aba8-f245ca97999a").split('\n')[1::] if rar[0:3] == "leg" else "")}}{{set("roll", vroll("1d48" if rar[0:3] == "com" else "1d96" if rar[0:3] == "unc" else "1d107" if rar[0:3] == "rar" else "1d72" if rar[0:3] == "ver" else "1d45" if rar[0:3] == "leg" else "0"))}} -desc "~~                                                                                                                                   ~~" -f "Roll | {{roll}}" -f "Loot| {{items[roll.total]}}" -footer "Awarding Magic Items | XGtE 139-145 & DMG 144-215" -color ede15e  
!item {{items[roll.total]}}  
```  
  
**Use With:** ``!loot`` (for common), ``!loot uncommon``, ``!loot rare``, ``!loot very``, ``!loot legendary``  
  
Feel free to @ or PM me if you find any issues or have any questions.