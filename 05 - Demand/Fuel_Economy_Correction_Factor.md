---
Source: https://leap.sei.org/help24/Demand/Fuel_Economy_Correction_Factor.htm
---

# Fuel Economy Correction Factor

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stocks](Stocks.md), [Sales](Sales.md), [Mileage](Mileage.md), [Fuel Economy](Fuel_Economy.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a [Transport Analysis](Transport_Analysis.md) for a demand technology.   Technology branches at which transport analyses are being conducted are shown in the tree marked with the transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).

The Fuel Economy Correction Factor variable is primarily useful when modeling U.S. vehicles in which the data on fuel economy provided by the Federal Government reflects a level of fuel economy that can be achieved in laboratory tests.  Typically this value is higher than real-world levels of fuel economy that can be achieved on the road. A correction factor of about 0.8 is generally used to convert from "rated" to "on-road" fuel economies.  Keep the default correction factor of 1.0 if your original fuel economy data reflects on-road conditions.

In LEAP's calculations, the [Fuel Economy](Fuel_Economy.md) variable is combined with the fuel economy degradation profile data and processed in LEAP's stock turnover calculations to yield the stock average rated fuel economy.  This value is then multiplied by the fuel economy correction factor to yield the stock average on-road fuel economy result.