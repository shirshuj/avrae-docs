**Testing For Arguments**  
*By zhu.exe#4211*  
  
Here is a simple snippet of code to test whether or not you have an argument passed to your alias. Replace ``"yes"`` with the code run when there is an argument, and ``"no"`` with the code run when there isn't an argument. Replace ``n`` with the argument number, such as ``1`` for the 1st argument.  
  
```GN  
{{"no" if "%n%" == "%n" + "%" else "yes"}}```