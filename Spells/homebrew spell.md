# Homebrew Spell Lookup
*By Croebh#5603 and silverbass#2407*

Allows you and your users to lookup your homebrew spells within avrae. Does *not* allow you to cast them, simply reference.
  
`!hspell` to list spells  
`!hspell [name]` to search  
`!hspell list [name]` to list all spells containing `[name]`  

### Setup
Simply make a gvar containing a list of spells using the following format:

```json
{
  "name": "Name of the spell",
  "level": "spell level and class requirements", 
  "action": "casting time", 
  "range": "range of the spell",
  "components": "components of the spell",
  "duration": "duration of the spell", 
  "desc": "description of the spell (use \n for new lines)",
  "ritual": "yes if ritual, blank if not",
  "upcast": "information about upcasting, blank if none"
}
```

For example, this is one with 1 spell:
```json
[
  { 
    "name": "Croebh's Homebrew Summonings",
    "level": "9th-level conjuration (Domini Aliorum, Bard (Aliaser))", 
    "action": "1 action", 
    "range": "30 feet",
    "components": "V, S, M (a gently used d20 worth $0.75, which the spell consumes)",
    "duration": "Instantaneous", 
    "desc": "You conjure a homebrew spell.\n\nIt is very good",
    "ritual": "yes",
    "upcast": ""
  }
]
```
and replace `YOUR GVAR HERE` with the id of your spell list!  
For an example list, you can use `cc0b3f7c-e042-4d2f-8299-231b78f7cdbc`, which contains homebrew spells by silverbass.

### Code
```GN
!alias hspell embed {{q,m,g='\n',"&1&".lower() in"list",load_json(get_gvar('YOUR GVAR HERE'))}}{{n="&2&".lower() if m else"&1&".lower() if "&"+"1&"!="&1&" else ""}}{{m=m or not n}}{{s=[i for i in g if n in i.name.lower()]}}{{s=s[0] if s and not m else [x.name for x in g] if m and not n else [x.name for x in s]}}
{{(f'-f "{s.name}|*{s.level}*" -f "Casting Time|{s.action}" -f "Components|{s.components}" -f "Range|{s.range}" -f "Duration|{s.duration}" -f "Ritual|{"yes" if s.ritual else "no"}" -f "Description|{s.desc}"'+(" -f \"At Higher Levels|"+s.upcast+"\"" if s.upcast else "")) if s and not m else f'-f "List of Spells Containing `{n}`|{q.join(s) if s else "No Matches Found"}"'}}
-color <color>
```
