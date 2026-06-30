---
Source: https://leap.sei.org/help24/Demand/Activity_Level_Analysis.htm
---

# Activity Analysis

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Demand Analysis](Demand.md) , [Useful Energy Demand Analysis](Useful_Energy_Analysis.md)

In this, the default methodology, energy consumption is calculated as the product of an [activity level](Activity_Level.md) and an annual [energy intensity](Energy_Intensity.md) (energy use per unit of activity). Overall activities are defined as the products of the individual activities entered along a complete branch of the Demand tree. Typically, activities are specified as a single absolute value (e.g. number of households) multiplied by a series of shares or saturations/penetrations (e.g. the percent share of urban households, the penetration of an end-use such as air conditioning), and the penetration of each technology that meets the end-use.

Total energy consumption is thus calculated by the equation:

energy consumption = activity level x energy intensity

There are two basic variations to this methodology: in a [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md) you specify energy intensities at the device level as the amount of fuel used per unit of activity; in a [Useful Energy Demand Analysis](Useful_Energy_Analysis.md) you specify useful energy intensities at the next highest branch level (typically the end-use level), and then specify the efficiencies of each device.

Note: this method can also be used to project energy consumption directly (i.e. not per unit of activity). To do this, simply enter "No data" for the units in the Activity Level variable.

Tip: use the methodology tab on the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up an Activity Analysis for a demand device.