---
Source: https://leap.sei.org/help24/Transformation/Fuel_Costs.htm
---

# Fuel Cost

See
also: [Analysis
View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md),
[Cost
Calculations](../01%20-%20Introduction/Transformation_Cost_Calculations.md)

Fuel Costs can be entered for each feedstock fuel and each auxiliary
fuel of each process. Fuel costs are used in calculating the [module
cost balance](../17%20-%20Results%20Categories/Module_Cost_Balance.md) result type and the costs of production result type and
are also used in calculating the optimized least-cost capacity expansion
and dispatch in scenarios, Note however that this variable is not directly
used in calculating the [social
cost](../17%20-%20Results%20Categories/Costs.md) result type.

To encourage consistency, the default expression for Transformation
fuel costs is set equal to the indigenous production costs specified in
the resource branches.  You can override this expression if you wish.
 You may want to do that if the fuels used in your Transformation
module are imported rather than being domestically produced or if the
fuel costs paid by the operators of your Transformation processes do not
match the costs used in your social cost-benefit analysis.

Note: Cost
data is shown only if the Cost
check box is checked in the [Module Properties](Module_Properties_Wiziard.md) screen and if costs
are enabled on the Scope tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen.