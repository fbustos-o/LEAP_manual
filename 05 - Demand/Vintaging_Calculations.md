---
Source: https://leap.sei.org/help24/Demand/Vintaging_Calculations.htm
---

# Transport Analysis Calculations

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stock Analysis](Stock_Analysis.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a [Transport Analysis](Transport_Analysis.md) for a demand technology.   Technology branches at which transport analyses are being conducted are shown in the tree marked with the transport icon (![](../assets/images/NewButtons/Tree/vehicle.png)).

For a given branch, the following equations describe the transportation calculations:

### Stock Turnover

![](../assets/images/Demand/eqStock1.gif)

![](../assets/images/Demand/eqStock3.gif)

Where:

 t is the type of vehicle (i.e. the technology branch)   
v is the vintage (i.e. the model year)  
y is the calendar year  
T is the number of types of vehicles  
Sales: is the number of vehicles added in a particular year: entered as an [expression](../01%20-%20Introduction/Expressions.md).  
Stock is the number of vehicles existing in a particular year: either entered as an [expression](../01%20-%20Introduction/Expressions.md) for Current Accounts or calculated internally based on historical sales.  
Survival is the fraction of vehicles surviving after a number of years: entered as a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md).  
V is the maximum number of vintage years: determined automatically from the survival [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md), with a maximum of 30 years.

For example, the remaining stock of government cars built in 1990 in the calendar year 2000 will be the sales of those cars in 1990 times the fraction that survive 10 years (2000-1990).

### Fuel Economy

![](../assets/images/Demand/eqFuelEconomy.gif)

Where:

FuelEconomy is fuel use per unit of vehicle distance traveled (i.e. 1/MPG). Entered as an [expression](../01%20-%20Introduction/Expressions.md).  
FeDegradation is a factor representing the decline in fuel economy as a vehicle ages. It equals 1 when y=v. Entered as a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md).

### Mileage

![](../assets/images/Demand/eqMileage.gif)

Where:

Mileage is annual distance traveled per vehicle. Entered as an [expression](../01%20-%20Introduction/Expressions.md).  
MlDegradation is a factor representing the change in mileage as a vehicle ages. It equals 1 when y=v. Entered as a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md).

### Energy Consumption

### 

### Distance-Based Pollution Emissions (e.g. Criteria Air Pollutants)

![](../assets/images/Demand/eqEmiss1.gif)

Where:

P is any criteria air pollutant.  
EmissionFactor is the emissions rate for pollutant p (e.g. grammes/ veh-mile) from new vehicles of vintage v. Entered as an [expression](../01%20-%20Introduction/Expressions.md).  
EmDegradation is a factor representing the change in the emission factor for pollutant p as a vehicle ages. It equals 1 when y=v. Entered as a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md).

### Energy-Based Emissions (e.g. CO2 and other Greenhouse Gases)

![](../assets/images/Demand/eqEmiss2.gif)

Emission results are calculated and then displayed in the [Results](../02%20-%20Views/Results_Screen.md) View.