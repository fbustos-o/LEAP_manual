---
Source: https://leap.sei.org/help24/Demand/Sales.htm
---

# Sales and Sales Share

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stock Analysis](Stock_Analysis.md), [Stocks](Stocks.md), [First Sales Year](First_Sales_Year.md)

The Sales variable is only available when conducting a stock-turnover analysis.  There are two types of stock-turnover analysis: one specific to vehicles (a [Transport Analysis](Transport_Analysis.md)) and another for all other types of devices (a standard [Stock Analysis](Stock_Analysis.md)).

A stock turnover analysis is useful in situations where you want to more accurately model how a newly introduced energy efficiency or emissions standards for sales of new technologies will translate into gradually improving overall average values across the total stock of devices (as new devices gradually replace older ones).

In stock-turnover analyses, Stocks and Sales data can either be specified at the technology branches (indicated by the ![](../assets/images/NewButtons/Tree/vehicle.png) icon in a transport analysis or the ![](../assets/images/NewButtons/Tree/Stock.png) icon in a standard stock analysis) or they can be specified using a top-down approach by entering total stocks and sales at the top level branches immediately below the Demand branch and then allocated down to the lower level technology branches using the Stock Share and Sales Share variables.  You can choose between a top-down approach or a bottom-up from the Stocks tab of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Stocks) screen.

The Sales variable is used to specify the addition of new devices on or after the [First Sales Year](First_Sales_Year.md).  Sales are specified in conjunction with a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) called the Survival Profile which  describes how devices are gradually retired as they get older.  These lifecycle profiles are specified for each technology when editing the sales data in Current Accounts.

Tip: For years before the First Sales Year, any sales data is ignored.  Stocks are simply entered as data.