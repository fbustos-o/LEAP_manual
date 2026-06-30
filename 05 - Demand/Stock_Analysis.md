---
Source: https://leap.sei.org/help24/Demand/Stock_Analysis.htm
---

# Stock Turnover Analysis

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Stock Analysis Calculations](Stock_Analysis_Calculations.md), [Transport Analysis Calculations](Vintaging_Calculations.md), [Stocks](Stocks.md), [Sales](Sales.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a stock turnover analysis.   There are two variations of this approach.  One for conducting transportation sector stock turnover modeling and another suitable for any other type of energy-using technology.  A stock turnover approach is most suitable when energy-using devices have fairly long lifetimes so that any changes to the marginal energy intensities and emission factors of newly introduced devices will thus take some time to affect the average energy intensities and emission factors of the total installed stock of devices.  The stock turnover method is also useful if the the operating characteristics of energy-using devices are subject change over the lifetime of those devices.  For example, older vehicles may be driven less (have lower mileage) than newer vehicles or there emission factors may increase (for example as the pollution control equipment starts to fail).  LEAP allows you to specify [Lifecycle Profiles](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) for variables that describe how such relevant variables change as devices get older.

When conducting a Transport stock turnover analysis, create branches with transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).  For non-transport stock turnover analyses, choose the green stock icon (![](../assets/images/NewButtons/Tree/Stock.png)).

Transport models:

With this methodology, energy consumption is calculated as the product of the number of vehicles, the annual average mileage (i.e. distance traveled) and fuel economy (e.g. liters per km or 1/MPG). The base year stock of vehicles is either entered directly or calculated from historical vehicle sales data and a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) describing survival rates as vehicles age. In scenarios, you can enter projections for future sales of vehicles, and for future levels of fuel economy, vehicle mileage and environmental loadings of newly added vehicles. You can also specify scrappage policies. Other lifecycle profiles are used to describe how mileage, fuel economy and environmental loadings change as vehicles age. LEAP calculates the stock average values for fuel economy, mileage and environmental loadings across all vintages and hence, ultimately, the overall level of energy consumption and environmental loadings.

Total energy consumption is calculated by the equation:

energy consumption = stock of vehicles x annual vehicle mileage x fuel economy

Note: Unlike with other demand analysis methods, which only allow emission factors to be specified per unit of energy consumed (e.g., kg/TJ), a Transport stock turnover analysis also allows you to specify emission factors per unit of distance traveled by a vehicle (e.g. grammes/veh-mile), which is often more appropriate for regulated transport sector pollutant emissions. For more information, please refer to [Transport Analysis Calculations](Vintaging_Calculations.md).

Stock Turnover for Other Energy Using Equipment

With this methodology, energy consumption is calculated by analyzing the current and projected future stocks of energy-using devices, and the annual energy intensity of each device. In Current Accounts, you specify the current stock of devices and the current stock-average energy intensity and environmental loadings. In scenarios, you project future additions (sales) of devices and the energy intensity and environmental loadings associated with those newly added devices. LEAP then calculates the stock average energy intensity and environmental loadings across all vintages and hence, ultimately, the overall level of energy consumption and environmental loadings.

Total energy consumption is calculated by the equation:

energy consumption = stock of devices x energy intensity per device