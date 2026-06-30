---
Source: https://leap.sei.org/help24/Transformation/Auxiliary_Fuel_Use.htm
---

# Auxiliary Fuel Use

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Feedstock Fuels](Feedstock_Fuel_Shares.md), [Efficiency](Efficiency_Data.md) [Calculation of Systems with Feedback Flows](Calculation_of_Transformation_Systems_with_Feedback_Flows.md)

For each process you can specify one or more auxiliary fuels. Auxiliary fuels are specified as energy consumed per unit of energy consumed or produced in a process. Unlike [feedstock fuels](Feedstock_Fuel_Shares.md), auxiliary fuels are NOT converted in a process, and hence their energy content is not included in how the overall [energy efficiency](Efficiency_Data.md) of the process is calculated. Auxiliary fuels are a useful of way of representing subsidiary or own-use energy consumption in a Transformation process, such as electricity used in an oil refinery or own-use of electricity in a power plant.

For each auxiliary fuel you can also specify environmental effects, by creating a link on the [Environment](../05%20-%20Demand/Environmental_Analysis.md) tab to a technology listed in the [TED database](../21.3%20-%20TED/TED_Intro.md).

Just as with a feedstock fuel, the use of an auxiliary fuel in a process creates a further requirement for that fuel to be supplied from somewhere else. By default, LEAP assumes that auxiliary fuels are supplied by transformation modules located lower down in the tree, or ultimately by imports.  However, if the auxiliary fuel being consumed is also produced by the process then you can treat that auxiliary fuel as "own use" consumption as shown in the diagram below.

![](../assets/images/Transformation/AuxFuelUse.gif)

To allow a module's processes to take auxiliary fuels from its own outputs, you will need to switch on the option marked Meet auxiliary fuel use from this module's outputs (where possible), which is located in each [Transformation Module's Properties screen](Module_Properties_Wiziard.md).  Note that you can set this option separately for each Transformation module.

There are a few points to consider when enabling this option:

1.  If a module's outputs are insufficient to meet the module's auxiliary fuel needs, then LEAP will attempt to meet any remaining requirements for the auxiliary fuels from lower down Transformation modules or from imports.

2.  Any emission factors applied to auxiliary fuel use will be applied to all of the auxiliary fuel use - including fuel produced internally in the module and fuels coming from lower down modules or imports.

3.  When using this option, note that any own use of fuels will not be apparent in LEAP's energy balance reports since the fuels are considered to be internal to a process. However, you can use the [Outputs by Output Fue](../17%20-%20Results%20Categories/Outputs.md)l and [Inputs](../17%20-%20Results%20Categories/Inputs.md) reports in [Results View](../02%20-%20Views/Results_Screen.md) to get information about own use in processes. Use the Input Type and Output Type dimensions to see information about how outputs are split between production for auxiliary fuel use and net production and how inputs are split among feedstock fuels, auxiliary fuels coming from outputs, and auxiliary fuels coming from other modules (or inputs).

4. Note that it may be quite common for an auxiliary fuel to be consumed in one module but to be produced only by a higher up module.  For example, an oil refinery module may consume electricity, which is produced only by an electricity generation module that is higher up in the list of Transformation modules.  If so, the system will need to iterate its calculations to ensure that the extra needs of the lower down modules are met by additional production in the higher up modules.  Refer to the section describing [Calculation of Systems with Feedback Flows](Calculation_of_Transformation_Systems_with_Feedback_Flows.md) for more information on this topic.