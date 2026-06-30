---
Source: https://leap.sei.org/help24/API/Functions_Editor.htm
---

# Functions Editor

Menu option: Advanced: Edit Functions  
See also: [CALL function](../18%20-%20Expressions/Call.md)

In addition to LEAP's built-in library of functions, you can also write your own functions in standard scripting languages such as VBScript, JScript, or Python.  These functions can be accessed from your expressions using the [CALL function](../18%20-%20Expressions/Call.md).  The functions editor lets you edit the default VBScript file (functions.vbs), which is stored in the current area folder.  Thus, you can have different functions specified in different areas.  More information on [Windows VBScript](http://msdn2.microsoft.com/en-us/library/ms950396) is available here.

A trivial example function is shown here:

Function Add(x,y)  
Add = x + y  
End Function

Notice that each function starts with the keyword Function and ends with the Keywords End Function.  Function results are set by assigning values to the function name (in this case Add).  LEAP functions should always return numeric values (integer or floating point) and should always use numeric parameters.  Functions can have any number of parameters, but the onus is on the user to pass the correct number of parameters in a comma separated list in the [CALL statement](../18%20-%20Expressions/Call.md).

In the functions editor, use the ave button (![](../assets/images/NewButtons/save.png))to save the functions.  The editor supports standard editing options such as cut (![](../assets/images/NewButtons/Cut.png)), copy (![](../assets/images/NewButtons/Copy.png)), paste (![](../assets/images/NewButtons/Paste.png)), undo (![](../assets/images/NewButtons/Undo.png)),  and find (![](../assets/images/NewButtons/find.png)).