---
Source: https://leap.sei.org/help24/Transformation/Capacity_Value.htm
---

# Capacity Credit

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Maximum Availability](Maxiumum_Capacity_Factor.md), [Endogenous Capacity](Endogenous_Capacity.md), [Exogenous Capacity](Capacties.md)

Capacity credit is defined for a process as the fraction of the rated capacity considered firm for the purposes of calculating the module [reserve margin](Planning_Reserve_Margin.md). For thermal power plants, the value normally shouldn’t exceed average annual [Maximum Availability](Maxiumum_Capacity_Factor.md). Lower values can be used for intermittent renewable power plants reflecting their lower average availability. Some plants assumed to have no firm capacity can even have zero capacity credit (for example imported electricity may sometimes have no firm capacity).

When specifying [endogenous capacity](Endogenous_Capacity.md), make sure that at least some of the plants in a module have a capacity credit greater than zero. Endogenous capacity is added to maintain the specified planning reserve margin, so any plants with zero capacity credit will not contribute at all to the reserve margin.

*Tip: To a first order of approximation, the capacity credit of a renewable plant can be assumed to be equal to the ratio of the availability of the renewable plant to the availability of a standard thermal plant.*