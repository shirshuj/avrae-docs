**Testing for Numbers**  
*By Toothless#7854*  
  
Snippet of code to test if a variable or input is a number or not.   
  
Replace ``"yes"`` with the code run when there is an argument, and ``"no"`` with the code run when there isn't an argument. Replace ``n`` with the argument number, such as 1 for the 1st argument.  
  
```py  
{{"yes" if "%n%".lstrip("-+").isdigit() else "no"}}  
```