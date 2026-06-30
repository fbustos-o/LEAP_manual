---
Source: https://leap.sei.org/help24/Demand/Mileage_Correction_Factor.htm
---

# Mileage Correction Factor

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Demand Analysis](Demand.md) , [Transport Analysis](Transport_Analysis.md) , [Stocks](Stocks.md) , [Sales](Sales.md) , [Fuel Economy](Fuel_Economy.md) , [Mileage](Mileage.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a [Transport Analysis](Transport_Analysis.md) for a demand technology.   Technology branches at which transport analyses are being conducted are shown in the tree marked with the transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).

Overall vehicle mileage is calculated based on the data you specify for the mileage of new vehicles and the mileage degradation profile that describes how annual miles driven decreases as vehicles get older.  These values are processed in LEAP's stock turnover calculations to yield the annual average mileage driven across the whole vehicle stock existing in each year.

Finally, you can also specify a mileage correction factor to adjust the mileage value calculated for the total vehicle stock.  This correction factor can be useful if you wish to create a model that examines driving rebound effects in which the miles driven in ALL vehicles (not just new vehicle) are responsive to certain policy variables such as the cost of gasoline.