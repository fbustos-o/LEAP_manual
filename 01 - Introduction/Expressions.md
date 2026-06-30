---
Source: https://leap.sei.org/help24/Concepts/Expressions.htm
---

# Expressions

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Examples of Expressions](../02%20-%20Views/Examples_of_Expressions.md), [Expression Builder](../21.6%20-%20Wizards%20and%20Properties/Expression_Builder.md), [Time-Series Wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md), [Expression Elaboration](../18%20-%20Expressions/Expression_Elaboration.md), [Specifying Excel File and Range Parameters](../18%20-%20Expressions/Excel_Ranges.md), [Referencing Results in Expressions](../18%20-%20Expressions/Results_Filters.md)

LEAP borrows an approach made popular in spreadsheets: the ability for users to enter data and construct models using mathematical expressions. Expressions are mathematical formulae used to specify the values of variables in LEAP's [Analysis View](../02%20-%20Views/Data_View.md). In Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year. an expressionA mathematical formula used to specify how the values of a variable changes from year to year. defines the historical values for a given variableData that can change over time. at a branchAn item on the tree. Different types of branches are represented by different icons on the tree, while in scenarios, the expression defines how that variable changes over time from the First Scenario Year to the End Year of the study period.

Expressions can range from simple numeric values to complex mathematical formulae. Each formula can optionally use LEAP's many built-in functions as well as referencing the values of other data and results variables. Expressions can also dynamically reference the values stored in an external Excel spreadsheet.

## Editing Expressions

LEAP provides a number of ways of editing expressions. The most common are:

* Typing directly into the expression field in one of the data entry tables in LEAP's [Analysis View](../02%20-%20Views/Data_View.md), or using the [Expression Builder](../21.6%20-%20Wizards%20and%20Properties/Expression_Builder.md) tab, in the lower half of the Analysis View screen.
* Selecting one of the commonly used functions: [Interpolation](../18%20-%20Expressions/Remainder.md) (![](../assets/images/NewButtons/TimeWiz/Interp.png)), [Growth](../21.6%20-%20Wizards%20and%20Properties/Growth_Dialog.md) (![](../assets/images/NewButtons/Growth.png)), [End-Year](../21.6%20-%20Wizards%20and%20Properties/End_Year_Dialog.md) (![](../assets/images/NewButtons/EndYear.png)), or [Remainder](../18%20-%20Expressions/Remainder.md) (![](../assets/images/NewButtons/sum.png))using the pop-up selection box attached to each expression field and marked by the ![](../assets/images/NewButtons/Exp%20Button.png) button.
* Using the [Time-Series Wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) (Ctrl+T or ![](../assets/images/NewButtons/TimeSeriesWizard.png)): a tool for easily entering time-series functions ([Interpolation](../18%20-%20Expressions/Interp.md), [Step](../18%20-%20Expressions/Step.md), [Smooth](../18%20-%20Expressions/Smooth.md) functions, and forecasting functions)
* Using the [Function Wizard](../16%20-%20Supporting%20Screens/FunctionWizard.md): (Ctrl+F or ![](../assets/images/NewButtons/Analysis.png)) a tool that helps you add functions into your expressions and complete the required parameters for each function.
* Using the [Branch/Variable Wizard](../16%20-%20Supporting%20Screens/Branch_Variable_Picker.md) (Ctrl+B) a tool that lets you create a reference to another branch and variable as well as specifying units and filters (for references to Results variables).

## Expression Inheritance

Nearly all data in LEAP are specified as expressions for a given variable at a given branch in the LEAP tree.  These expressions are entered in LEAP's [Analysis View](../02%20-%20Views/Data_View.md) and different expressions can be entered for different scenarios (or for different regions in a multi-region area).  To minimize data entry requirements and to make data management as easy as possible, scenarios are organized in a hierarchy so that you need only enter data in one scenario if it differs from the data entered in its parent (ancestor) scenario. Before describing the scenario manager, it is important to first understand the way that expression inheritance works in LEAP since this is fundamental to understanding how scenarios help you manage data. See [Understanding Expression Inheritance](Understanding_Expression_Inheritance.md) for more information.

To reset an expression back to its inherited default, highlight the expression and press Delete, or right-click and select the Reset to Inherited (![](../assets/images/NewButtons/Delete.png)) option.  .

## Expression Color Coding

When editing scenario data in LEAP's [Analysis View](../02%20-%20Views/Data_View.md), LEAP color codes expressions to show which were entered explicitly, and which were inherited from another scenario or another region.

* Purple text indicates an expression has been entered explicitly in the scenario currently being edited.
* Black text indicates that a value is inherited from another scenario or another region.
* Green text indicates an expression is inherited from another region (in a multi-region data set).
* Silver text indicates that you are using the default expression for the variable (i.e. that nothing has explicitly been entered in Current accounts or any other region or scenario).  You can edit the default expressions for a variable by right-clicking on the variable tab, and then edit its Properties.
* Red italicized text indicates that the expression contains an error.

Note: in Analysis view you can also use the Tree: Show Scenario Branches option to list and optionally jump to any of the branches entered explicitly in the current scenario.

## Referencing Variables in Expressions

In addition to using expressions to directly specify data, you can also create expressions that refer to the values of other variables in LEAP.  In this way you can create your own models that include both exogenous (externally specified) data and endogenous (internally calculated) variables.

You can reference both data variables and results variables.  Data variables are those that are specified directly in LEAP's Analysis View through LEAP's expressions. Results variables are the additional values calculated internally by LEAP.  Results variables include values such as total final energy demand, total emissions or total costs, as well as many other types of results.

Because they are calculated internally, in general, you can only reference results that were calculated in a previous year. This is done by using the [PrevYearValue](../18%20-%20Expressions/PrevYearValue.md) function to reference a past value of a result variable.  An exception is when specifying calculated [Indicator](../14%20-%20Indicators/Indicators.md) variables.  Because these are calculated after LEAP's main calculation routines they may include references to the present-year value of results variables.

You can create references to data variables by dragging and dropping items from the Analysis View tree into the Expression Builder, by using LEAP's built-in code completion features, or by using the [Branch/Variable Wizard](../16%20-%20Supporting%20Screens/Branch_Variable_Picker.md) (Ctrl+B).

For more information on how to create references to other variables, see these two pages:

* [Referencing Data and Constants in Expressions](../18%20-%20Expressions/Referencing_Other_Data_Variables_in_Expressions.md)
* [Referencing Results in Expressions](../18%20-%20Expressions/Results_Filters.md)

## Expression Elaboration ()

[Expression Elaboration](../18%20-%20Expressions/Expression_Elaboration.md) is a feature that elaborates the various branches and variables upon which the current expression depends.  Expression elaboration is implemented as a tab on a panel under the main data entry table in Analysis View to elaborate complex expressions.   Expression Elaboration is useful for helping you to understand and explain your analyses without continually having to navigate from branch to branch in the tree.  You can disable Expression Elaboration by right-clicking within the [Analysis View](../02%20-%20Views/Data_View.md) data entry table and choosing Expression Elaboration.

Expression Elaboration shows the branches and variables upon which the current expression depends,  and also lists the branches, variables and scenarios that depend on the current branch.  Double-click one of the listed items to jump directly to that branch and variable.