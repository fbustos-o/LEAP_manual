---
Source: https://leap.sei.org/help24/Demand/Demand.htm
---

# Demand Analysis

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md) , [Useful Energy Demand Analysis,](Useful_Energy_Analysis.md) [Demand Cost Analysis](Demand_Cost_Analysis.md) , [Environmental Analysis](Environmental_Analysis.md)

Demand analysis is a disaggregated, end-use based approach for modeling the requirements for final energy consumption in an AreaThe energy system being studied . You can apply economic, demographic and energy-use information to construct alternative scenarios that examine how total and disaggregated consumption of final fuels evolve over time in all sectors of the economy. You can also examine the [costs](Demand_Cost_Analysis.md) and [environmental implications](Environmental_Analysis.md) of each scenarioA self-consistent story line of how a future energy system might evolve over time in a particular socio-economic setting and under a particular set of policy conditions. . Energy demand analysis is also the starting point for conducting integrated energy analysis, since all Transformation and Resource calculations are driven by the levels of final demand calculated in your demand analysis.

LEAP provides a lot of flexibility in how you structure your demand data. These can range from highly disaggregated end-use oriented structures to highly aggregateTo summarize by grouping together. analyses. Typically a structure would consist of sectors including households, industry, transport, commerce and agriculture, each of which might be broken down into different subsectors, end-uses and fuelSomething combusted, or otherwise used to produce energy -using devices. You can adapt the structure of the data to your purposes, based on the availability of data, the types of analyses you want to conduct, and your unit preferences. Note also that you can create different levels of disaggregation in each sector.

Similarly, you also have choices in the methodologies you can apply for energy demand analysis. The following methodologies are available

![](../assets/images/NewButtons/Tree/technology.png) [Activity Level Analysis](Activity_Level_Analysis.md), which itself consists of either [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md), or [Useful Energy Demand Analysis](Useful_Energy_Analysis.md) in which energy consumption is calculated as the product of an activity level and an annual energy intensity (energy use per unit of activity).

![](../assets/images/NewButtons/Tree/Stock.png) [Stock Analysis](Stock_Analysis.md), in which energy consumption is calculated by analyzing the current and projected future stocks of energy-using devices, and the annual energy intensity of each device (defined as energy per device).

![](../assets/images/NewButtons/Tree/vehicle.png) [Transport Analysis](Transport_Analysis.md), in which energy consumption is calculated as the product of the number of vehicles, the annual average mileage (i.e. distance traveled per vehicle) and the fuel economy of the vehicles (e.g. liters per km or 1/MPG).

You can mix and match these different methodologies within a single data set: for example applying useful energy analysis for the analysis of industrial and commercial heating and employing final energy analysis for all other sectors.

In each case, demand calculations are based on a disaggregated accounting for various measures of social and economic activity (number of households, vehicle-km of travel, tonnes of industrial production, commercial value added, etc.) These "activity levels" are multiplied by the energy intensities of each activity (energy per unit of activity). Each activity levelA measure of social and economic activity. When used in LEAP's Demand analysis, activity levels are multiplied by energy intensities to yield overall levels of energy demand and energy intensityThe average energy consumption of some device or end-use per unit of activity. can be individually projected into the future using a variety of techniques, ranging from applying simple exponential growth rates and interpolation functions, to using sophisticated modeling techniques that take advantage of LEAP's powerful built-in modeling capabilities.