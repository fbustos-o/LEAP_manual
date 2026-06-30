---
Source: https://leap.sei.org/help24/Demand/Stocks.htm
---

# Stock and Stock Share

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stock Analysis](Stock_Analysis.md), [Sales](Sales.md), [First Sales Year](First_Sales_Year.md)

The Stock variable is only available when conducting a stock-turnover analysis.  There are two types of stock-turnover analysis: one specific to vehicles (a [Transport Analysis](Transport_Analysis.md)) and another for all other types of devices (a standard [Stock Analysis](Stock_Analysis.md)).

A stock turnover analysis is useful in situations where you want to more accurately model how a newly introduced energy efficiency or emissions standards for sales of new technologies will translate into gradually improving overall average values across the total stock of devices (as new devices gradually replace older ones).

In stock-turnover analyses, Stocks and Sales data can either be specified at the technology branches (indicated by the  ![](../assets/images/NewButtons/Tree/vehicle.png) icon in a transport analysis or the ![](../assets/images/NewButtons/Tree/Stock.png) icon in a standard stock analysis) or they can be specified using a top-down approach by entering total stocks and sales at the top level branches immediately below the Demand branch and then allocated down to the lower level technology branches using the Stock Share and Sales Share variables.  You can choose between a top-down approach or a bottom-up from the Stocks tab of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Stocks) screen.

The Stock variable is used to initialize a stock turnover calculation by specifying the total number of devices at the start of the calculation.  The stock variable is used in conjunction with a [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) called the Stock Vintage Profile, which describes how the total stock of devices is distributed among devices of each different vintage (i.e. new devices, one year-old devices, two-year-old devices, etc.).  These lifecycle profiles are specified for each technology when editing the stock data in Current Accounts.

The Stock variable is used in conjunction with the [First Sales Year](First_Sales_Year.md) variable, which sets the year in which the stock turnover calculation begins.  Before this year, LEAP only uses the Stock variable to specify the total stock of devices.  After the First Sales Year, the stock of devices is calculated according to LEAP's stock turnover calculations, taking into account the future [Sales](Sales.md) of new devices and the retirement of older devices, as well as any forced [scrappage](Scrappage.md) of devices.

Please note the following when entering stock data.

* For years before the First Sales Year, enter the total stock of devices at the end of each year including the devices added (i.e. sales) in that year.
* For the First Sales Year, enter the stock at the start of the year - i.e. NOT including the sales in the first sales year.
* Values entered for the Stock variable are ignored after the First Sales Year.

Tip: if your First Sales Year is set to the base year (the default), then you should only enter a single value for Stocks: the stock at the start of the base year NOT including the sales in the base year.