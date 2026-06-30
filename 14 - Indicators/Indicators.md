---
Source: https://leap.sei.org/help24/Indicators/Indicators.htm
---

# Indicators

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Indicator Functions](../18%20-%20Expressions/IndicatorFunctions.md), [Key Assumptions](../21.6%20-%20Wizards%20and%20Properties/Macrovariable_Properties_Wizard.md)

Indicators are special branches in the [Tree](../03%20-%20Interface/TreeOverview.md) that can be used to calculate additional user-defined results.  All Indicator branches are created under the high level Tree branch named Indicators which appears as the last major category of branches in the tree.  Under this branch, you can create your own category (![](../assets/images/NewButtons/folder.png))and indicator (![](../assets/images/NewButtons/Tree/In.png)) branches.  Category branches are simply used to organize other branches.  When adding indicator branches, you must specify a measurement unit for each variable as text.

By default the high level Indicators branch is not visible.  To show this branch, go to the Scope tab on the [General: Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen and check the Indicators check box.

Indicators work in a similar fashion to [Key Assumptions](../21.6%20-%20Wizards%20and%20Properties/Macrovariable_Properties_Wizard.md).  That is, they are a place where you can define your own variables.  Just as with Key Assumptions, Indicators are not used directly in LEAP's calculation routines.  However, unlike other variables, Indicators are only updated after LEAP's calculations are complete.  Therefore, unlike other variables, Indicators can include non-lagged references to LEAP's results variables.  This makes them a good place for calculating additional energy sector indicators that compare certain key indicators across regions and scenarios.  LEAP includes a series of [Indicator Functions](../18%20-%20Expressions/IndicatorFunctions.md) that can be used in your [expressions](../01%20-%20Introduction/Expressions.md) to help you calculate such comparisons.  Note however that because Indicators are calculated last, regular data variables may not reference indicator variables.  Another important difference between indicators and other variables is that, because they are calculated after results, changing an indicator expression in a scenario does not force the all of the scenario's results to be recalculated.

The following table summarizes the differing capabilities of Indicators and other variables.

|  |  |
| --- | --- |
| Indicators | Other Variables |
| Can reference all data variables  e.g.: Demand\Household:Activity Level | Can only reference non-indicator variables |
| Can reference result variables  e.g.:  Freedonia:Global warming potential C eq. | Can only reference lagged value of result variables.  For example:  PrevYearValue(Freedonia:Global warming potential C eq) |
| Not used directly in LEAP's calculations and cannot be referenced by other non-indicator branches. | Not used directly in LEAP's calculations but can be referenced by other non-indicator branches that ARE included in LEAP's calculations. |
| Changes to indicator expressions do not cause scenarios to be recalculated. | Any change to an expression causes all related scenarios to recalculate. |

Note: in addition to defining variables under the Indicators category, you can also add your own [User Defined Variables](../16%20-%20Supporting%20Screens/User_Variables.md) within the Indicator branches.  These can be useful for doing additional calculations such as normalizing and weighting variables that you wish to compare across regions or scenarios.  Use the General: [User Variables](../16%20-%20Supporting%20Screens/User_Variables.md) screen to define your own User Variables.