# Boulder-parchment-shears
*By Karew#3333*

Lets a player throw a random choice in Boulder-parchment-shears (AKA Rock–paper–scissors). The alias doesn't enforce the rules or keep track of results, it just lets people throw a random result without cheating.

For reference, the rules are:

1. At least two players must throw a choice. Then the choices are compared.
2. Boulder crushes shears, shears cuts parchment, and parchment covers boulder.
3. If players throw the same result, it's a tie, and usually they re-throw.

### Usage

Run `!bps`

### Code

```GN
!servalias bps embed {{bps={0:"boulder",1:"parchment",2:"shears"}[randint(3)]}} -thumb "<image>" -desc "{{name}} plays boulder-parchment-shears and throws **{{bps}}**"
```
