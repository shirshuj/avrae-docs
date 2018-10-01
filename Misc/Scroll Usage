**Scroll Usage**

Alias to perform ability check to cast from a scroll. Figures out ability mod on it's own.
Can also be used to do the ability check for a Wizard to copy a scroll.

Use with:
`!scroll 6`
`!scroll 9`
`!scroll 7 copy` for Wizard copying

```
!alias scroll !multiline
{{args="%1%%2%%"}}{{args=args[:args.index("%")]}}
{{wizCopy="copy" in args or "book" in args or "wiz" in args}}
{{args=''.join([i for i in args if i.isdigit()])}}
{{spellLvl=int(args) if args.isdigit() else 5}}
{{dc=spellLvl+10}}
{{stats=[charismaMod, intelligenceMod, wisdomMod]}}
{{check="arc" if wizCopy else ["char", "int", "wis"][stats.index(max(stats))]}}
{{title=f"Copy a level {spellLvl} Spell." if wizCopy else f"Cast a level {spellLvl} Spell!"}}
!check {{check}} -title "<name> Attempts to {{title}}" -dc {{dc}} &*&
```
