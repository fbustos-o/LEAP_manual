---
Source: https://leap.sei.org/help24/Expressions/Expression_Elaboration.htm
---

# Expression Elaboration

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Expressions](../01%20-%20Introduction/Expressions.md)

Expression Elaboration is a tab in Analysis View marked by the ![](../assets/images/NewButtons/Elaboration.png) button.  This tab shows two lists: the variables referenced by the current expression and the variables which themselves reference the current expression.

Double-clicking on any item in these lists will make the display jump to the listed branch/variable.

Expression Elaboration is useful for helping you to understand and explain your analyses WITHOUT continually having to navigate from branch to branch in the tree.  The list on the left traces back through all the variables referenced in the currently selected expression and either showing the values of those variables, or if they themselves are calculated, by tracing back further to subsequently referenced variables. Dependent variables are shown indented by a few lines in the list.