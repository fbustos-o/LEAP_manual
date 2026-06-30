---
Source: https://leap.sei.org/help24/Results_Categories/Reserve_Margin.htm
---

# Reserve Margin (%)

See also: [Results View](../02%20-%20Views/Results_Screen.md)  
Result Type: Transformation

This results category shows the amount of reserve margin in a given module. This variable is generally only relevant for electricity generation modules.  This variable is only reported if you have specified capacity data for the module.   Results can be shown organized by branch, scenario, year and region (in multi-regional areas).

Reserve margin is defined as follows:

Reserve Margin (%) = 100 * (Module Capacity - Peak Load) / Peak Load

Where:

Module Capacity = Sum([Capacity](../08%20-%20Transformation/Capacties.md) * [Capacity Value](../08%20-%20Transformation/Capacity_Value.md)) for all processes in the module.

Peak load is calculated based on the requirements for electricity and the module load factor (which may itself be based on the shape of a module load curve). Electricity requirements are calculated based on your energy demand analysis and any upstream electricity losses (for example in a Transmission and Distribution module).

Reserve margin may not be the same as the data you entered for the [Planning Reserve Margin](../08%20-%20Transformation/Planning_Reserve_Margin.md).  Assuming that you have specified certain processes that will be added automatically using the [Endogenous Capacity](../08%20-%20Transformation/Endogenous_Capacity.md) screen, then the actual reserve margin reported here should be greater than or equal to the planning reserve margin.  This is because LEAP automatically adds new plants as needed in order to keep your reserve margin on or above your planning reserve margin.  On the other hand, if plants are not being added automatically and if you have not [exogenously](../08%20-%20Transformation/Capacties.md) specified sufficient capacity expansion, then it is possible that the actual reserve margin may fall below the planning reserve margin.