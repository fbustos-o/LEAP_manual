---
Source: https://leap.sei.org/help24/Demand/Fuel_Economy.htm
---

# Fuel Economy

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stocks](Stocks.md), [Sales](Sales.md), [Mileage](Mileage.md), [Fuel Economy Correction Factor](Fuel_Economy_Correction_Factor.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a [Transport Analysis](Transport_Analysis.md) for a demand technology.   Technology branches at which transport analyses are being conducted are shown in the tree marked with the transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).

Use this screen to specify the fuel economy of newly purchased vehicles of a given vehicle type (![](../assets/images/NewButtons/Tree/vehicle.png)). Fuel economy is defined as energy consumption per unit of vehicle-distance traveled (or its inverse in the case of MPG).

In Current accounts, you can select among various standard units for specifying fuel economy data including miles per gallon (US and UK versions) and Liters Per KM. You will also need to select the fuel used by the vehicle. You can also optionally specify a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) describing how fuel economy worsens as vehicles age. Take special care with this profile. In the case of MPG fuel economy data this should be a constant or decreasing profile, while in the case of data specified in Liters per KM, the profile should be constant or increasing. If you do not have information on how fuel economy changes as vehicles age, simply leave the profile set to its default value of Constant.

When entering fuel economy data, the software can also help you convert values from one unit to another. Simply enter the value in one unit (e.g. MPG) and then select another unit (e.g. Liters/100 KM). LEAP will ask you if you wish to convert the value you entered. Notice also that you can enter data in any unit, and even mix units within an analysis. The software will automatically convert units to a common base unit during calculations, at which point you will also be able to review results in a wide range of different units.

The fuel economy data you enter, should represent the on-road fuel economy of newly purchased vehicles. Based on this data and the data you specified concerning vehicle stocks, sales and survival, LEAP will automatically calculate the stock average fuel economy. In the lower half of the screen you can use the toolbar shown below to display either New Vehicle Fuel Economy or Stock Average Fuel Economy values as a chart or table. You can also use the toolbar, to view the data in different units including MPG (US and UK), Liters per 100 KM or KW-hr per 100 KM (useful for electric and hydrogen/fuel cell vehicles).

When specifying Current Accounts fuel economy data, it can be important to specify historical values so that the software can accurately calculate the correct base year stock average value. If you simply specify a single value for the fuel economy of vehicles sold in the base year, then the software will assume that same value also applies to all vehicles sold in previous years. You can use [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to create an [Interp](../18%20-%20Expressions/Interp.md) function that specifies historical data for fuel economy.