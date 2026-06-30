---
Source: https://leap.sei.org/help24/Wizards_and_Properties/Expression_Builder.htm
---

# Expression Builder

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Expressions,](../01%20-%20Introduction/Expressions.md) [Examples of Expressions](../02%20-%20Views/Examples_of_Expressions.md)

## Introduction

The Expression Builder let's you edit a single expression in a larger space than the single rows shown in the [Analysis View](../02%20-%20Views/Data_View.md) data table.  This is particularly useful for editing  complex equations spread over multiple rows.  You can add your own line breaks and indentation spaces in the Expression Builder to make complex equations easier to read.  This formatting will be preserved when you save the expression back into the Analysis View table.  Note that when viewing a muti-line expression in the data table, line breaks will appear written as the "~" character.  The Expression Builder also let's you quickly access pages of help while editing an expression, simply move the cursor over any function name and the lower pane of the Expression Builder will display a page of help for the appropriate function.

The Expression builder supports multiple techniques for creating and editing expressions.  These include:

* Directly typing an expression
* Using various software wizards to select and add elements to an expression.
* Dragging and dropping branches from the main tree to add branch/variables references to an expression.
* Using code completion (autocomplete) to assist you in typing branch/variable references.

## Context-Sensitive Help

When editing an expression in the Expression Builder, as the moves among different keywords, LEAP will automatically detect any function names and display the help page for that function in a pane on the right-hand side of the Expression Builder.  If you don't want to see this, simply click the hot spot on the splitter bar to hide the help pane.

## Wizards

While editing an expression in the Expression Builder you can use additional wizards to help you to create your expressions.  These wizards include:

1. * The [Function Wizard](../16%20-%20Supporting%20Screens/FunctionWizard.md) (Ctrl+F)
   * The [Time-Series Wizard](Time_Series_Wizard.md) (Ctrl+T)
   * The [Branch/Variable Wizard](../16%20-%20Supporting%20Screens/Branch_Variable_Picker.md) (Ctrl+B).

Each of these wizards will pop-up to help you to create the elements of an overall expression.   Note that you can also edit the elements of an existing screen using these wizards.  To edit a function or a branch/variable reference place the cursor within one of these elements and press Ctrl-Space.  The appropriate wizard will be displayed allowing you to edit either the function or the branch/variable reference.

## Drag and Drop

The Expression Builder also supports dragging and dropping branches and variables from the tree.  When you drop a branch on the tree, a popup window will appear from which you can select one of the variables associated with the dropped tree branch.

## Code Completion (Autocomplete)

You can also quickly add branches and variables using code completion.  Start by typing in the first element of the branch name (e.g. "Key" for a key variable or "Demand" for a demand branch) then type the "\" path separator character.  LEAP will pop up a window from which you can select among the branches immediately underneath the branch you first entered (as shown in the attached figure). Once you have entered the complete path to a branch, type  ":" and LEAP will popup the list of valid data and results variables at that branch.  After selecting a variable type "[" and LEAP will popup the list of valid units in which that variable can be referenced.  If you are using Aliases to define a partial branch name, then you can also type in an alias followed by the "\" or ":" characters and LEAP will display a popup from which you can select a branch or variable.

If you do not want to use code completion, you can switch it off by right-clicking in the Expression Builder (or in an expression in the data table above) and unchecking the **Autocomplete** option.