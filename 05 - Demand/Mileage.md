---
Source: https://leap.sei.org/help24/Demand/Mileage.htm
---

# Mileage

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stocks](Stocks.md), [Sales](Sales.md), [Fuel Economy](Fuel_Economy.md), [Mileage Correction Factor](Mileage_Correction_Factor.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a [Transport Analysis](Transport_Analysis.md) for a demand technology.   Technology branches at which transport analyses are being conducted are shown in the tree marked with the transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).

Use this screen to specify the mileage of newly purchased vehicles of a given vehicle type (![](../assets/images/NewButtons/Tree/technology.png)). Mileage is defined as annual distance traveled per vehicle.

In Current accounts, you can select among various standard distance units (or you can even add your own on the [Units](../16%20-%20Supporting%20Screens/Units.md) screen). You can also optionally specify a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) describing how mileage changes as vehicles age. If you do not have information on how mileage changes as vehicles age, simply leave the profile set to its default value of Constant.

Based on the mileage data you specify for newly purchased vehicles and the data you specified concerning vehicle [stocks](Stocks.md), [sales](Sales.md) and survival, the software will automatically calculate the stock average mileage. In the lower half of the screen you can use a toolbar to display either New Vehicle Mileage or Stock Average Mileage values as a chart or table.

When specifying Current Accounts mileage data, it can be important to specify historical values so that the software can accurately calculate the correct base year stock average value. If you simply specify a single value for the mileage of vehicles sold in the base year, then the software will assume that same value also applies to all vehicles sold in previous years. You can use [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to create an [Interp](../18%20-%20Expressions/Interp.md) function that specifies historical data for mileage.