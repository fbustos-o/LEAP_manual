---
Source: https://leap.sei.org/help24/Supporting_Screens/Branch_Variable_Picker.htm
---

# Branch/Variable Wizard

See also: [Expressions](../01%20-%20Introduction/Expressions.md), [Referencing Data in Expressions](../18%20-%20Expressions/Referencing_Other_Data_Variables_in_Expressions.md), [Referencing Results in Expressions](../18%20-%20Expressions/Results_Filters.md)

## Introduction

The branch/variable wizard (![](../assets/images/NewButtons/Tree/folder.png)) is a popup wizard used to select a specific variable at a particular branch in the [LEAP tree](../03%20-%20Interface/TreeOverview.md).

## Using the Branch/Variable Wizard

The wizard is made up of 2 or 3 pages depending on the type of branch.  The first page shows a view of the LEAP tree, from which you can select a particular branch.

![](../assets/images/NewScreens/BranchVarPicker1.png)

Once you select a branch and select Next, the second page shows a list of the valid variables at the selected branch.  You can select both data variables (the Tabs in Analysis View) and result variables, whose values are calculated when you show the Results, Summary and Energy Balance views.  When creating expressions, typically you can only create references to lagged results variables, since these depend on the values of data variables. More information here on [referencing data variables](../18%20-%20Expressions/Referencing_Other_Data_Variables_in_Expressions.md) and [referencing results variables](../18%20-%20Expressions/Results_Filters.md) in expressions.

![](../assets/images/NewScreens/BranchVarPicker2.png)

Once you select a variable and select Next, in some situations a third page will be shown on which you can choose a scaling factor and unit for the reference to the branch/variable. You can also select filters for the reference.  For example, if you create a reference to total social costs at the highest level area branch, you can filter the results to return the value for only a particular cost category (e.g. fuel import costs or capital costs).  The list of allowable filter dimensions depends on the variable you choose.  Data variables can only be filtered by tag, while Results variables can be filtered by different dimensions such as fuel, region, effect, category, etc.

![](../assets/images/NewScreens/BranchVarPicker3.png)

Once you have chosen a branch, variable, units and (optionally) filters, click Finish to confirm your selection.  If you are in the process of creating an expression, your selection will be written into your expression. For example, for the options selected in the above screenshots, the expressions would appear as "Freedonia:Social Costs[Billion USD, Cost category=Fuel imports]".

Click Cancel at any point to abandon the wizard without making a selection.