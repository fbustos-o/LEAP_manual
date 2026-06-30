---
Source: https://leap.sei.org/help24/Demand/Transport_Analysis.htm
---

# Transport Analysis

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis Calculations](Vintaging_Calculations.md), [Stocks](Stocks.md), [Sales](Sales.md)

energy consumption = stock of vehicles x annual vehicle mileage x fuel economy

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a Transport Analysis for a demand technology.   Technology branches at which transport analyses are being conducted are shown in the tree marked with the transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).

With this Demand Analysis methodology, energy consumption is calculated as the product of the number of vehicles, the annual average mileage (i.e. distance traveled) and fuel economy (e.g. liters per km or 1/MPG). The base year stock of vehicles is either entered directly or calculated from historical vehicle sales data and a lifecycle profile describing survival rates as vehicles age. In scenarios, you can enter projections for future sales of vehicles, and for future levels of fuel economy, vehicle mileage and environmental loadings of newly added vehicles. Other lifecycle profiles are used to describe how mileage, fuel economy and environmental loadings change as vehicles age. LEAP then calculates the stock average values for fuel economy, mileage and environmental loadings across all vintages and hence, ultimately, the overall level of energy consumption and environmental loadings.

Note: Unlike the other two demand analysis methods, which only allow emission factors to be specified per unit of energy consumed (e.g., kg/TJ), the Transport Analysis method also allows you to specify emission factors per unit of distance traveled by a vehicle (e.g. grammes/veh-mile), which is often more appropriate for regulated transport sector pollutant emissions.

For more information, please refer to [Transport Analysis Calculations](Vintaging_Calculations.md)