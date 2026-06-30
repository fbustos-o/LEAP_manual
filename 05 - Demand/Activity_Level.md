---
Source: https://leap.sei.org/help24/Demand/Activity_Level.htm
---

# Activity Levels

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md), [Final Energy Intensity](Final_Energy_Intensity.md), [Useful Energy Demand Analysis,](Useful_Energy_Analysis.md) [Demand Cost Analysis](Demand_Cost_Analysis.md)

Activity Levels are used in LEAP's Demand analysis as a measure of the social or economic activity for which energy is consumed.

In creating a demand analysis structure, you typically create a hierarchy of branches, in which activity levels are described in absolute terms (e.g., number of households) at one level of the hierarchy, and in proportionate terms (e.g. percentage share or percentage saturation) terms in the other levels of the hierarchy. The product of these terms yields the overall level of activity for a given deviceA type of demand branch, which contains information about a fuel-using technology. : one of the leaf branches in a Demand tree. Energy consumption in the device is then calculated by multiplying the overall level of activity for the device by its energy intensityThe average energy consumption of some device or end-use per unit of activity..

Notice that in some cases energy intensities can be defined at the end-use level, rather than the device level. Nevertheless, the general principle holds that LEAP calculates energy consumption as the product of activity levels and energy intensities.