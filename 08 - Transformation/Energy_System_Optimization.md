---
Source: https://leap.sei.org/help24/Transformation/Energy_System_Optimization.htm
---

# Energy System Optimization

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Introduction to Optimization](../21.2%20-%20Optimization/OptimizationIntroduction.md)

This variable, specified the top level (area) branch, is used to control whether the energy sector is calculated in a given scenario using LEAP's full energy system optimization calculations.

If set to No, calculations will either be done using LEAP's simulation methodologies or using partial optimization for a particular Transformation module.

You can control which scenarios use optimization by changing this variable in different scenarios.  When this variable is set to Yes, LEAP will use NEMO along with the fastest solver installed on your PC.

Use the [Yes function with additional parameters](../18%20-%20Expressions/Yes.md) to specify particular solvers or to enable limited foresight optimization.

Note that you cannot conduct optimization calculations for Current Accounts and so this variable is only available in scenarios (not in Current Accounts).