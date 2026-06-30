---
Source: https://leap.sei.org/help24/Transformation/Capital_Costs.htm
---

# Capital Cost

See
also: [Analysis
View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md),
[Cost
Calculations](../01%20-%20Introduction/Transformation_Cost_Calculations.md), [SalvageValue](Salvage_Value.md)

Note: Cost data is shown only if
the Cost check box is checked
in the [Module
Properties](Module_Properties_Wiziard.md) screen and if costs are enabled on the Scope tab of the
[Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md)
screen. You may enter cost data for any processA Transformation branch that describes an individual technology or group of technologies within a module such as a particular electric plant or oil refinery. However, for a comparative
analysis of scenarios, you need only enter costs for processes which differ
(in terms of energy consumption, production or installed capacity) among
scenarios.

Capital costs should reflect the total (i.e.,
non-annualized) capital costs per unit of capacity of each process.  Capital
costs should include all direct construction costs (i.e. [overnight
costs](http://en.wikipedia.org/wiki/Overnight_Capital_Cost)) and any capitalized finance costs. Use the selection boxes
at the top of the screen to select a scale and unit for the data.

The costs you enter here are later annualized
during LEAP's calculations, based on the [lifetime](Lifetime.md)
of each process, and the [interest rate](Interest_Rate.md)
charged on the capital cost.  LEAP allows you to choose among different
methods for annualizing capital costs.  You can do this on the Costs
tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Costing_Methodology)
screen.  The available methods are:

* Capital
  Recovery Factor (the default method)
* No
  Annualization
* Straight
  Line Depreciation
* Sinking
  Fund Depreciation
* Declining
  Balance Depreciation
* Double
  Declining Balance Depreciation

These approaches are used to spread capital
costs over the lifetime of each process,  Capacity additions specified
endogenously will automatically be replaced after each lifetime (and thus
will incur recurring capital costs. Capacity additions specified
exogenously do not get automatically replaced.

When constructing scenarios that use LEAP's
least-cost [optimization](../21.2%20-%20Optimization/OptimizationIntroduction.md)
methods, you must choose the Capital Recovery Factor method.