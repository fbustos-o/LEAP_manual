---
Source: https://leap.sei.org/help24/Demand/Useful_Energy_Analysis.htm
---

# Useful Energy Demand Analysis

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md)

Tip: use the [Demand Branch Properties](Demand_Properties_Wizard.md) dialog to set-up a useful energy demand analysis.

For cases in which you wish to explicitly consider demand-side efficiency improvements and fuelSomething combusted, or otherwise used to produce energy switching independently of the evolution of useful energy demands (e.g. the heat demand in a building), you may wish to use LEAP's useful energy analysis methodology instead of the default [final energy analysis](Final_Energy_Demand_Analysis.md).

A useful energy analysis lets you independently consider three important trends: a) how the overall useful demand might change over time (for example as incomes rise and people consume more, or as building standards improve affecting heat demand per square meter), b) how the market penetration of different devices changes over time, and c) how the efficiencies of devices (i.e. final energy demand per unit of useful energy provided) is likely to evolve over time.

To configure a useful energy analysis, do the following:

1. Add a Category with Energy Intensity branch type (![](../assets/images/NewButtons/Tree/FolderGreen.png)) at the end-use level (e.g. heating, cooling, cooking).
2. On the [Demand Branch Properties](Demand_Properties_Wizard.md) screen, check the box marked "useful energy analysis" and click OK.  
   ![](../assets/images/NewScreens/UsefulEnergyAnalysis1.png)
3. Below this branch add additional technology branches (![](../assets/images/NewButtons/Tree/Technology%20Green.png)) to represent the various fuel-using devices that are available to meet the demands of the end-use. Note that useful energy branches are always immediately above the technology branches in a demand tree. Only technology branches may be added below them. In the example shown on the right, three substitute fuels (fuel oil, electricity and natural gas) area used to provide commercial heating.

## Current Accounts

When conducting a useful energy analysis, Current Accounts data can be specified in two different ways:

1. In the default method, you specify final energy intensities for the end-use, along with the [fuel shares](Fuel_Share.md) and [efficiencies](Efficiencies.md) for each fuel or deviceA type of demand branch, which contains information about a fuel-using technology. level. Notice that device fuel shares are not the same thing as the activity shares entered in a final energy analysis. Fuel shares are the share of total final energy consumed by each device, while activity shares reflect the number of "activities" (e.g. the share of floor space heated by different boiler types). The percentage efficiencies you enter for each device are used to calculate the overall useful energy intensity for the end-use, and the activity shares for each device in the Current Accounts year. This first approach is most useful when you have Current Accounts data describing the total fuel consumed in the base year, and you wish LEAP to calculate the useful energy demand.
2. In the second method, you specify useful energy intensities directly in Current Accounts. This approach is useful in cases where you have data describing the useful demand for a branch (e.g. the heat demand in buildings).

Tip: use the [Demand Branch Properties](Demand_Properties_Wizard.md) dialog to select between these two alternatives. Notice that you can mix and match methods freely in different branches

## Scenarios

Irrespective of the method you choose for Current Accounts, in scenarios you project the useful energy demand, device efficiencies and activity shares into the future.