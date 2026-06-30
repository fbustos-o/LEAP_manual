---
Source: https://leap.sei.org/help24/Transformation/Optimized_Capacty.htm
---

# Optimized New Capacity

See
also: [Analysis
View](../02%20-%20Views/Data_View.md) , [Transformation Analysis](Transformation.md),
[Exogenous Capacity](Capacties.md), [Endogenous
Capacity](Endogenous_Capacity.md)

The
Optimized Capacity variable is a read-only
variable that is only available in scenarios where you are using LEAP's
optimization methodology to calculate future capacity of processes.  The
expression stored in the variable is calculated internally during LEAP's
calculations.

Use the [Optimize](Optimize.md)
variable (specified at the module level) to specify whether a scenario
is optimized or not.  A single area may have some scenarios that
are optimized and others in which you specify capacity using the [Exogenous
Capacity](Capacties.md) and [Endogenous Capacity](Endogenous_Capacity.md)
variables.