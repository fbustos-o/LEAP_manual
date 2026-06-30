---
Source: https://leap.sei.org/help24/Affordability/Fuel_Price.htm
---

# Fuel Price

See also:

Fuel Price is a variable only used as part of LEAP's optional [Affordability Analysis](../02%20-%20Views/Affordability_Reports.md) calculations.

The variable specifies the price paid for any of the fuels included in an affordability analysis.  You can specify fuel prices as a simple value, perhaps accompanied in scenarios by a growth rate, or you can specify fuel prices using the [Tariff function](../18%20-%20Expressions/Tariff.md), which lets you specify the billing period, fixed costs and different block rate tariffs.  You can also specify fuel prices using a time-series function if you want to specify how costs vary by season or by time of day.

You will see one fuel price variable for each fuel included in your affordability analysis at the branches marked as **Affordability Branches**via the [Demand Properties](../05%20-%20Demand/Demand_Properties_Wizard.md) dialog.  Affordability analysis is enabled in the [Settings: Scope](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) screen.  Use the Affordability column in the [Fuels screen](../16%20-%20Supporting%20Screens/Fuels.md) to choose which fuels are included in your affordability analysis. Note that if you include certain fuels but those fuels are not consumed in any of the technology branches (![](../assets/images/NewButtons/Tech%20Gray.png)) below your affordability analysis branch, then you will not see a fuel price variable for those fuels.

Fuel prices are used to calculate overall energy-related costs borne by households and industry as part of the Affordability analysis in comparison against the annual income (or revenue) at the analysed branches.