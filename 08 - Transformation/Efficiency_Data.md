---
Source: https://leap.sei.org/help24/Transformation/Efficiency_Data.htm
---

# Process Efficiency, Losses and Heat Rates

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), Storage

ProcessA Transformation branch that describes an individual technology or group of technologies within a module such as a particular electric plant or oil refinery efficiency data can be specified in three different ways: as a percentage efficiency, as a heat rate or as the percentage energy losses. You can set which method you want to use, by editing the [module properties](Module_Properties_Wiziard.md). For storage processes, efficiency indicates the ratio of energy generated to energy stored in the process.

## Efficiency

The default method is to specify the percentage ratio of energy outputs (not including any co-product  energy recovered) to feedstockAn input fuel consumed by a Transformation conversion process. energy inputs in each process. All efficiencies must be greater than zero. When entering efficiencies for processes, around 33% is typical for base-load steam generation. This also may be used as a nominal value for hydro-electric stations so that primary resourceA fuel that has not been converted or processed such as coal, crude oil, hydropower, solar, wind, etc. requirements for fossil fuels and hydro can be easily compared. Another common approach is to use a 100% efficiency for hydropower and renewable electricity generation systems. If you specifically enter imports as one of the process types, enter 100% for their efficiencies.

## Heat Rate

Efficiency data can also be specified as a heat rate (the rate of feedstock fuelSomething combusted, or otherwise used to produce energy required per unit of energy produced - efficiency data is often expressed in this form for electricity plants).

## Losses

Efficiency can also be specified as the percentage of energy lost in a process. This approach can be useful for specifying transmission and distribution systems.