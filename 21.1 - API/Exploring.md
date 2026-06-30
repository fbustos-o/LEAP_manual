---
Source: https://leap.sei.org/help24/API/Exploring.htm
---

# Exploring the API Using MS-Excel

See also: [Automating LEAP with the API](API.md), [The Script Editor](Using_the_Script_Editor.md)

Microsoft Excel provides a useful environment for exploring the LEAP API, using its Visual Basic Editor. In Excel, first create a new blank workbook, then go to Tools: Macros: Visual Basic Editor.

Now go to Tools, References. Scroll down to find "LEAP" and make sure the check box is checked. You will only need to do this once for each workbook. Go to View, Immediate Window to open the "Immediate" window, a place for you to type in commands and see their results instantly. Try the following in the Immediate Window, one at a time:

|  |  |
| --- | --- |
| Set L = createobject("LEAP.LEAPApplication")  ? L.Areas.Count  L.ActiveArea = "Freedonia"  L.View = "Analysis"  ? L.ActiveScenario.Name  L.ActiveScenario = "Current Accounts"  L.Branch("\Demand\Household\Urban").Variables("Activity Level").Expression = 20  Msgbox("Paused to show a favorite")  L = nil | This will open LEAP and set a local variable "L" to reference it  How many areas do you have? The question mark is VB shorthand for PRINT  Opens Freedonia  Sets the Analysis View  Prints the active scenario name  Sets the active scenario to "Current Accounts"  Sets the expression used to define a variable at a branch  Pauses  Closes LEAP without saving any changes |

Excel can also remind you of the properties, methods and classes in the LEAP API, via its "Intellisense" technology. Intellisense only works when editing a macro, not in the Immediate Window. On the left side of the Excel Visual Basic Editor, double-click on "ThisWorkbook" to open the code window. Then on the menu, choose Insert, Procedure. Give it a name ("Test"), and you can now start adding code to it. On the first line, type

Dim L As

After you type "As" and a space, Excel will pop up a list from which can choose different properties. You can either scroll down to choose "LEAPApplication", or start typing this. After you type "LE", Excel will jump to that section of the list. Highlight LEAPApplication, then hit Enter to select it. For this to work, you must have already done the Tools, References step mentioned above. (If Excel isn't showing this list, hit Ctrl-Space to pop it up.)

Now that Excel knows that L is of type LEAPApplication, you can type "L." (that's L followed by a period) and a list will pop up of all the API properties and methods for the LEAPApplication class. On the next line, type "L." and choose ActiveArea from the list. Excel will move to the next line, but that line is not finished yet. Go back up to the L.ActiveArea line and type = "Freedonia" to finish it.

Another way that Excel can show the details of the API is in the "Object Browser." On the menu, choose View, Object Browser. In the top left of this window, change from <All Libraries> to LEAP. Now, you should see all the classes listed on the left. Click on a class, and its properties and methods will be listed on the right. Click on the property or method on the right and information about it will be displayed below. For example, click on LEAPApplication on the left, then ResultValue on the right. Below, you should see all the parameters that ResultValue needs, including those which are optional.