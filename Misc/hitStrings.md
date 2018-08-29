# Hit Strings and the Hit Command
*By @derixyleth.xls*

The `!hstring` alias sets up a cvar with a list of user-provided "hit strings" to be called randomly as titles by the `!hit` command, which takes the place of `!init attack`.

### Setup
No initial setup is required before running the `!hstring` alias. `!hstring` will give you further instructions. Can `add`, `del`ete, and `list` your hit strings. Once you have a list you're happy with, just use `!hit target weapon` when in init instead of `!init attack target weapon` and it'll randomly pull a hit string for the title of the attack. If you want to have separate strings for melee and ranged, just make another version called `!sstring`, switch the 'hit's to 'shoot's (if you care), change the cvar hStrings to sStrings (3 instances in each alias, mandatory), and then use whatever version depending on which weapon you're using.

### Code
`!hstring` for setting them up:
```
!alias hstring embed {{c,na="&1&",name.replace('"','\'\'')}}{{z="&*&".replace(c+' ','')}}{{H,A,D,L,dN=c=="help" or z=="",c=="add","del" in c,c=="list",int("&2&") if "&2&".isdigit() else "nope"}}{{set_cvar_nx("hStrings","[charname] attacks [target] with their [aname]!")}}{{hS=hStrings.split("~")}}{{hL=[str(x+1)+": \'"+hS[x]+"\'\n" for x in range(len(hS))]}}{{dS=hS[dN-1] if dN!="nope" else None}}{{hS.remove(dS) if dS and D and len(hS)>1 else hS.append(z) if A else ""}}{{'-title "'+na+('\'s Hit Strings" -desc "'+''.join(hL)+'"' if L else ' adds a new string to their list!" -desc "\''+z+'\' added to '+na+'\'s Hit Strings!"' if A else (' needs to supply a string number!" -desc "You need to tell this alias which string to delete."' if dN=='nope' else ('tries to delete' if len(hS)<2 else 'deletes')+' a hit string!" -desc "'+('You must have at least one hit string!"' if len(hS)<2 else '\''+dS+'\' removed from '+na+'\'s Hit Strings!"')) if D else ', here is how to use this command:" -desc "`[charname]`,`[aname]`, and `[target]` will autoreplace in your hit strings. To add a hit string, use `!hstring add [charname] does whatever with a [aname] to [target]!` replacing the nonbracketed text with whatever you want your custom message to be. To add multiple hit strings at once, separate them with a \'~\' (e.g. `!hstring add [charname] does whatever with a [aname] to [target]!~[charname] does something else to [target] with a [aname]!`) To see a list of your hit strings, use `!hstring list`. To delete a hit string, use `!hstring del #` where # is the number on the list of the hit string you want to delete. `!hstring help` or a plain `!hstring` brings up this help message. Hit Strings are called randomly by the `!hit` command."')}}{{set_cvar("hStrings",'~'.join(hS)) if A or D else ""}} -color <color> -thumb <image>
```

`!hit` for using them in combat:
```
!alias hit i a &*& {{' -title "'+hStrings.split("~")[randint(len(hStrings.split("~")))]+'"' if exists("hStrings") else ""}}
```
