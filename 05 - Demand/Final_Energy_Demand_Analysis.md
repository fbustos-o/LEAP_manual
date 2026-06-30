---
Source: https://leap.sei.org/help24/Demand/Final_Energy_Demand_Analysis.htm
---

# Final Energy Demand Analysis

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Useful Energy Demand Analysis](Useful_Energy_Analysis.md)

In conducting a final energy demand analysis, a typical approach is to disaggregateTo break something down into sub-categories (e.g. during end-use analysis of energy demands). your demand data structure into four levels representing sectors, subsectors, end-uses and devices. An example of this approach showing the Activity LevelA measure of social and economic activity. When used in LEAP's Demand analysis, activity levels are multiplied by energy intensities to yield overall levels of energy demand table in the [Analysis View](../02%20-%20Views/Data_View.md) is given below.

![](../assets/images/NewScreens/Final%20Energy%20Demand%20Analysis1.png)

Activity levels for one of the four hierarchical levels are typically described in absolute terms (in this case the number of households is 8 million in the Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year. year), while the other three levels are described in proportionate (i.e. percentage share or percentage saturation) terms. In the example shown above, urban households are 30% of the total number of households in 2000, of these 95% have some type of refrigerator, and all refrigerators are existing (less efficient) models. None of the new, more efficient models have been introduced in the base yearThe first historical year of a LEAP analysis. . Notice that at the top level, the user chose an absolute unit for the activity level (households). At lower levels, LEAP keeps track of the units, and hence knows that the percentage number entered at the second level is the share "of households". In general, LEAP lets you choose the numerator units for activity levels, whilst automatically displaying the denominator unit. When selecting an activity level unit, you can choose from any of the standard non-energy units. Use the Units screen ([Main Menu](../03%20-%20Interface/Menu.md): General Parameters: [Units](../16%20-%20Supporting%20Screens/Units.md)) if you need to add additional units.

The above data are shown for the Current Accounts year, but all values can be altered for future years in scenarios. This allows the planner to capture the combined effects of separate changes at many levels, such as, for example, the growth in the total number of households, the rate of urbanization, the penetration of refrigeration, and the market share of less efficient vs. more efficient refrigerator models. To project these data, you first use the Manage Scenarios option to create one or more scenarios. Then, in the Analysis View, you override the default (constant) expressions entered in Current Accounts for each branchAn item on the tree. Different types of branches are represented by different icons on the tree , with new expressions that describe how each value changes over time.

The tree structure for this type of final energy analysis is shown below.

![](../assets/images/NewScreens/Final%20Energy%20Demand%20Analysis2.png)

Notice that all of the branches are created as [category branches](../03%20-%20Interface/Types_of_Tree_Branches.md#Category) (![](../assets/images/NewButtons/Tree/folder.png)) except for the bottom-most nodes, which are always created as [technology branches](../03%20-%20Interface/Types_of_Tree_Branches.md#Technology) (![](../assets/images/NewButtons/Tree/Technology.png)). For these bottom-level branches, you also define the annual energy intensities per unit of activity level (in this case per household) and specify the fuels used by the deviceA type of demand branch, which contains information about a fuel-using technology. (see below).

![](../assets/images/NewScreens/Final%20Energy%20Demand%20Analysis3.png)

When editing [energy intensities](Energy_Intensity.md), first select the fuelSomething combusted, or otherwise used to produce energy used by each device and then set the scale and units in which you want to enter the intensity. The scale and units columns can only be edited in Current Accounts. Changes to the energy intensityThe average energy consumption of some device or end-use per unit of activity. units column subsequent to entering an intensity value will cause LEAP to offer to convert the value to the new units.