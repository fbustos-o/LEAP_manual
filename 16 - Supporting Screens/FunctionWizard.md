---
Source: https://leap.sei.org/help24/Supporting_Screens/FunctionWizard.htm
---

# Function Wizard

![](../assets/images/NewScreens/FunctionWizard.png)

## Introduction

The Function Wizard is a popup tool that helps you to write the expressions that define the data and models entered in LEAP's [Analysis View](../02%20-%20Views/Data_View.md).

## Using the Function Wizard

The Function Wizard can be invoked when creating an expression by clicking Ctrl-F or by selecting Function from the drop-down menu attached to every expression in the Analysis View data tables.  It can also be invoked in a similar way from the [Expression Builder](../21.6%20-%20Wizards%20and%20Properties/Expression_Builder.md) tool.  The function wizard can also be invoked by clicking a function in an existing expression and pressing Ctrl-Space or Ctrl-F.

The Function wizard is displayed as a popup dialog containing a series of selection and edit boxes.

* Function Type: This selection box is used to select among different classes of functions.  LEAP has over one hundred  functions that you can include in your expressions divided into five main categories: modeling functions, mathematical functions, logical functions, statistical functions, and financial functions.  The Functions Wizard also lets you create references to the properties of the fuels located at branch in the LEAP tree, and references to constant values, created in the General:  [Constants](Constants.md) screen.
* Function: The Function selection box is used to select a specific function from a drop down menu.  The  functions are listed alphabetically and filtered by the class of functions selected in the Function Type selection box. To see all functions, choose All in the Function Type selection box.

Once you have selected a specific function, the wizard displays a short description of that function. More detailed help on the function including detailed syntax and examples of how it can be applied are available by clicking the More button to expand the window.  Below the function name, a series of edit boxes are displayed in which you can specify the parameters required by the Function.    Parameters can either be specified as simple numeric values or they can be entered using a series of additional popup windows that are used to select [LEAP branch/variable references](Branch_Variable_Picker.md), [Excel spreadsheet ranges](Excel_Range_Picker.md) or time series of values (selected using the [Time-Series Wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md)).  Each parameter is also described in detail.

When the Function wizard is invoked with the cursor placed within an existing function, then the Function Wizard will be displayed with the function wizard populated with the parameters for that function.

As you enter the data for each parameter, LEAP will check those parameters.  Errors in parameter specifications are highlighted in red text.  A preview of the function and its parameters and its evaluated numeric value are shown at the top of the Function Wizard.  Once the required minimum set of parameters has been completed, you can press the OK button to add the completed function to your overall expression.