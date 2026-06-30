---
Source: https://leap.sei.org/help24/Transformation/Stranded_Costs.htm
---

# Stranded Costs

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Cost Calculations](../01%20-%20Introduction/Transformation_Cost_Calculations.md)

Stranded Costs represent any remaining costs to be paid on existing processes (typically debt payments on old capital). These processes are typically specified using the [Exogenous Capacity](Capacties.md) Variable.  Unlike other Transformation costs, stranded costs are specified as total amounts (not a value per MW or per MW-Hr).  Use the [LoanPayment](../18%20-%20Expressions/LoanPayment.md) function if you want to calculate the future annual payments based on the total capital cost, the year of the loan, the term and the rate of interest charged.  Typically stranded costs are only specified for Current Accounts as they do not apply to processes that will be built in the future.

The Stranded Costs you enter are used in the calculation of the [Module Cost Balance](../17%20-%20Results%20Categories/Module_Cost_Balance.md). Because they represent a sunk cost they are not included in the [Social Costs](../17%20-%20Results%20Categories/Costs.md) result type.

Note: This variable is shown only if the Cost check box is checked in the [Module Properties](Module_Properties_Wiziard.md) screen and if costs are enabled on the Scope tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen. You may enter cost data for any processA Transformation branch that describes an individual technology or group of technologies within a module such as a particular electric plant or oil refinery. However, for a comparative analysis of scenarios, you need only enter costs for processes which differ (in terms of energy consumption, production or installed capacity) among scenarios.