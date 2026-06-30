---
Source: https://leap.sei.org/help24/Transformation/Planning_Reserve_Margin.htm
---

# Planning Reserve Margin

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Peak Load Ratio](Peak_Load_Ratio.md)

The planning reserve margin is specified at each Transformation module and is used by LEAP to decide when to automatically add additional [endogenous capacity](Endogenous_Capacity.md). LEAP will add enough additional capacity to maintain the planning reserve margin on or above the value you have set.

Planning reserve margin is defined as follows:

Planning Reserve Margin (%) = 100 * (Module Capacity - Peak Load) / Peak Load

Module Capacity = Sum([Capacity](Capacties.md) * [Capacity Value](Capacity_Value.md)) for all processes in the module.

Peak load is calculated based on the requirements for electricity and the module load factor (which itself is based on the shape of the [System Load Shape](../06%20-%20Load%20Shapes/System_Load_Shape.md)). Electricity requirements are calculated based on your energy demand analysis and any upstream electricity losses (for example in a Transmission and Distribution module).

Note: this variable was previously located at load shape branches. It is now located at Transformation modules.