**Divine Smite**  
*By Paranoid#8322.*  
Outputs smite in a way that matches the !spell output more closely.  
Usage: `!smite <slot lvl>` or `!critsmite <slot lvl>`  
```  
!alias smite multiline  
!embed -title "<name> channels a level %1% Divine Smite!" -desc "**Add. Damage**: 1d8 + %1%d8 ({{set("a", roll("1d8"))}}{{set("b", roll("1d8"))}}{{set("c", roll("1d8"))}}{{set("d", roll("1d8"))}}{{set("e", roll("1d8"))}}{{set("f", roll("1d8"))}}{{"**"+str(a)+"**" if a==8 or a==1 else a}},{{"**"+str(b)+"**" if b==8 or b==1 else b}}{{(",**"+str(c)+"**" if c==8 or c==1 else ","+str(c)) if %1% > 1 else ""}}{{(",**"+str(d)+"**" if d==8 or d==1 else ","+str(d)) if %1% > 2 else ""}}{{(",**"+str(e)+"**" if e==8 or e==1 else ","+str(e)) if %1% > 3 else ""}}{{(",**"+str(f)+"**" if f==8 or f==1 else ","+str(f)) if %1% > 4 else ""}}) [radiant] = {{a+b if %1%==1 else a+b+c if %1%==2 else a+b+c+d if %1%==3 else a+b+c+d+e if %1%==4 else a+b+c+d+e+f}}"  
!g ss %1% -1
```  

```GN
!alias critsmite multiline   
!embed -title "<name> channels a critical level %1% Divine Smite!" -desc "**Add. Damage**: 2d8 + {%1%*2}d8 ({{set("a", roll("1d8"))}}{{set("A", roll("1d8"))}}{{set("b", roll("1d8"))}}{{set("B", roll("1d8"))}}{{set("c", roll("1d8"))}}{{set("C", roll("1d8"))}}{{set("d", roll("1d8"))}}{{set("D", roll("1d8"))}}{{set("e", roll("1d8"))}}{{set("E", roll("1d8"))}}{{set("f", roll("1d8"))}}{{set("F", roll("1d8"))}}{{"**"+str(a)+"**" if a==8 or a==1 else a}},{{"**"+str(A)+"**" if A==8 or A==1 else A}},{{"**"+str(b)+"**" if b==8 or b==1 else b}},{{"**"+str(B)+"**" if B==8 or B==1 else B}}{{(",**"+str(c)+"**" if c==8 or c==1 else ","+str(c)) if %1% > 1 else ""}}{{(",**"+str(C)+"**" if C==8 or C==1 else ","+str(C)) if %1% > 1 else ""}}{{(",**"+str(d)+"**" if d==8 or d==1 else ","+str(d)) if %1% > 2 else ""}}{{(",**"+str(D)+"**" if D==8 or D==1 else ","+str(D)) if %1% > 2 else ""}}{{(",**"+str(e)+"**" if e==8 or e==1 else ","+str(e)) if %1% > 3 else ""}}{{(",**"+str(E)+"**" if E==8 or E==1 else ","+str(E)) if %1% > 3 else ""}}{{(",**"+str(f)+"**" if f==8 or f==1 else ","+str(f)) if %1% > 4 else ""}}{{(",**"+str(F)+"**" if F==8 or F==1 else ","+str(F)) if %1% > 4 else ""}}) [radiant] = {{a+A+b+B if %1%==1 else a+A+b+B+c+C if %1%==2 else a+A+b+B+c+C+d+D if %1%==3 else a+A+b+B+c+C+d+D+e+E if %1%==4 else a+A+b+B+c+C+d+D+e+E+f+F}}"  
!g ss %1% -1  
```