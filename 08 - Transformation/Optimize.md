---
Source: https://leap.sei.org/help24/Transformation/Optimize.htm
---

# Optimize

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Introduction to Optimization](../21.2%20-%20Optimization/OptimizationIntroduction.md), [Specifying Capacity Data](Specifying_Capacty_Data_in_LEAP.md)

This variable, specified at the level of an individual Transformation module is used to control switch on **partial optimization** - controlling whether a particular module's calculations for a given scenario are carried out using LEAP's optimization or simulation methodologies.

You can control which scenarios use optimization by simply editing the Optimize variable in LEAP in any given scenario.  When this variable is set to Yes, LEAP will use NEMO along with the fastest solver installed on your PC.  When set to No, LEAP will use its accounting and simulation calculations.

Use the [Yes function with additional parameters](../18%20-%20Expressions/Yes.md) to specify particular solvers or to enable limited foresight optimization.

You cannot conduct optimization calculations for Current Accounts and so this variable is only available in scenarios (not in Current Accounts).

If you switch on [Full Energy System Optimization](Energy_System_Optimization.md), then this variable will no longer appear and any settings for it will be ignored. That is, you cannot simultaneously do both **full** and **partial** energy system optimization in a single scenario.  However, you can use these different methods in different scenarios.

Only one module can be enabled for partial optimization.  If you set the Optimize variable to Yes in more than one module then LEAP will report an error during calculations.