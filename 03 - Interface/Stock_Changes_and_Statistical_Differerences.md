---
Source: https://leap.sei.org/help24/Screen_Layout/Stock_Changes_and_Statistical_Differerences.htm
---

# Stock Changes and Statistical Differences

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Tree](TreeOverview.md)

Data describing stock changes and statistical Differences are particularly useful for ensuring that your historical modeling in LEAP precisely matches published energy balance data for a country. Note however, that it is typically good practice to assume that these values are all set to zero in forward-looking scenarios.

In the [tree](TreeOverview.md), two additional top level branch categories labeled Stock Changes and Statistical Differences are visible if you select Statistical Differences and Stock Changes, on the Scope & Scale tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen.

* Stock Changes: under which you can specify supply of primary energy from stocks. Negative values indicate an increase in stocks. The values you specify will be added to the total primary supply of the fuel, and will appear as a separate row in the [energy balance](../02%20-%20Views/Energy_Balance_View.md) view between the Transformation and Resource sections.
* Statistical Differences: under which you can specify the differences between final consumption values and energy demand data. Typically, the data you enter in your Transformation analysis (e.g. imports and production of energy) will be derived from data provided by government or large energy producers (oil refineries, electricity companies, etc.), whereas your energy demand estimates may be based on end-use surveys. Often demand and supply data will be somewhat inconsistent. You can express the differences by entering data in the Statistical Differences tables. You can specify statistical differences for any fuel consumed in your area or any other secondary fuel produced. The values will be added to the final demand values calculated in your Demand analysis, and will appear as a row in the [energy balance](../02%20-%20Views/Energy_Balance_View.md) view between the Demand and Transformation sections. Enter a positive value to increase the energy demand or a negative value to decrease it.