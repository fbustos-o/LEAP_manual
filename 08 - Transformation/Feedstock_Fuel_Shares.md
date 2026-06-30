---
Source: https://leap.sei.org/help24/Transformation/Feedstock_Fuel_Shares.htm
---

# Feedstock Fuel Shares

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Auxiliary Fuel Use](Auxiliary_Fuel_Use.md), [Efficiency](Efficiency_Data.md)

Processes can have any number of feedstock fuels. Feedstocks are the fuels converted within the process itself, such that the efficiency of a process is defined as the ratio of the total energy content of all output fuels produced by the process divided by the total energy content of all feedstock fuels consumed. For each feedstock fuel, its fuel share is the percentage share of energy input it provides to its parent process. Typically, most process will have only one feedstock fuel, and hence the fuel share should be set to 100% in Current Accounts. Note that feedstock fuels are distinct from auxiliary fuels. Feedstocks are the fuels converted within the process, while auxiliary fuels are specified as energy consumed per unit of energy consumed or produced in a process. Auxiliary fuels reflect subsidiary fuel consumption in a process. They are NOT converted in a process, and hence their energy content is not included in how the overall energy efficiency of the process is calculated.

For each feedstock fuel you can also specify environmental effects, by creating a link on the [Environment](../05%20-%20Demand/Environmental_Analysis.md) tab to a technology listed in the TED database.