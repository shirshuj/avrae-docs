# Action Surge
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/2nTQe5P.png"/>
</p>

Automatically creates "Action Surge" counter if nonexistant. Subtracts 1 from "Action Surge" counter. Automatically increases "Action Surge" uses upon gaining Fighter levels.

### Usage

``!action``

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Code
```GN
!alias action embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("footer", "Fighter | PHB 72")}}
{{set("counter", "Action Surge")}}
{{set("ccMax", int(actionSurge) if exists("actionSurge") and actionSurge.isdigit() else 0)}}
{{set("lvl", int(FighterLevel) if exists("FighterLevel") else level)}}
{{set("addCounter", ccMax <= 1 and int(lvl) >= 17)}}
{{set_cvar("actionSurge", 1 if lvl < 17 else 2)}}
{{create_cc_nx(counter, 0, "actionSurge", "short", "bubble")}}
{{mod_cc(counter, addCounter)}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}}
-title "{{name}} {{"uses" if valid else "attempted to use"}} {{counter}}!"
-desc "{{"On your turn, you can take one additional action on top of your regular action and a possible bonus action." if valid else "Once you use this feature, you must finish a short or long rest before you can use it again. Starting at 17th level, you can use it twice before a rest, but only once on the same turn. (``!g sr``)"}}"
-f "{{counter}} | {{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
{{"-footer \"" + footer + "\"" if str(showpage) == "true" else ""}}
{{"-thumb " + str(image) if str(embedimage) == "true" and valid else ""}} 
-color <color>
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``action`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Multiclassing

If you are multiclassing and you are not using a DiceCloud sheet, run the following command, replacing ``$lvl$`` with your current fighter level.

```GN
!cvar FighterLevel $lvl$
```

**You must run this command every time you gain a fighter level.** If you do not do this, the alias will use your total level instead of your Fighter level. This may cause problems in your aliases.

### Variable List

These are the counters and variables this alias uses to function properly. **Do NOT delete them unless you plan to delete the alias as well.**

**`!cc "Action Surge"`** - Tracks the uses of Action Surge in a custom counter.

**`!cvar actionSurge`** - Sets the maximum value of Action Surge counter.

**`!cvar embedimage`** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage``** - Enables / disables whether subjects and page numbers are displayed.
