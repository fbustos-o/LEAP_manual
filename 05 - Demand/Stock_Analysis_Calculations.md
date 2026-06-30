---
Source: https://leap.sei.org/help24/Demand/Stock_Analysis_Calculations.htm
---

# Stock Analysis Calculations

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Stock Analysis](Stock_Analysis.md)

Use the [Demand Branch Properties](Demand_Properties_Wizard.md) screen to set-up a [Stock Analysis](Stock_Analysis.md) for a demand technology.   Technology branches at which stock analyses are being conducted are shown in the tree marked with the stock icon (![](../assets/images/NewButtons/Tree/Stock.png)).  For a given technology branch, the following equations describe the calculations for the stock analysis methodology:

### Stock Turnover

![](../assets/images/Demand/eqbasicstock.gif)

![](../assets/images/Demand/eqStock3.gif)

Where:

 t is the type of technology (i.e. the technology branch)  
v is the vintage (i.e. the year when the technology was added)  
y is the calendar year  
Sales: is the number of vehicles added in a particular year: entered as an [expression](../01%20-%20Introduction/Expressions.md).  
Stock is the number of devices existing in a particular year: either entered as an [expression](../01%20-%20Introduction/Expressions.md) for Current Accounts or calculated internally based on historical sales.  
Survival is the fraction of devices surviving after a number of years: entered as a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md).  
V is the maximum number of vintage years: determined automatically from the survival [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md), with a maximum of 30 years.

### Energy Intensity

![](../assets/images/Demand/eqEnIn.gif)

Where:

 EnergyIntensity is energy use per device for new devices purchased in year y. Entered as an [expression](../01%20-%20Introduction/Expressions.md).  
Degradation is a factor representing the change in energy intensity as a technology ages. It equals 1 when y=v. Entered as a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md).

### Energy Consumption

### 

### Energy-Based Emissions (e.g. CO2 and other Greenhouse Gases)

![](../assets/images/Demand/eqEmiss2.gif)

Emission results are calculated and then displayed in the [Results](../02%20-%20Views/Results_Screen.md) View.