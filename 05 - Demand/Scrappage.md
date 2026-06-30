---
Source: https://leap.sei.org/help24/Demand/Scrappage.htm
---

# Scrappage

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transport Analysis](Transport_Analysis.md), [Stock Analysis](Stock_Analysis.md), [Sales](Sales.md), [Stocks](Stocks.md), [Max Scrappage Fraction](Max_Scrappage_Fraction.md)

When conducting a [Transport Analysis](Transport_Analysis.md) or a [Stock Analysis](Stock_Analysis.md) for a demand technology (![](../assets/images/NewButtons/Tree/technology.png)) you can specify the number of devices or vehicles to be scrapped early.

The Scrappage variable specifies the total number of devices to be scrapped early (before they would normally be retired by the technology's specified survival profile).  Use this variable in conjunction with the [Max Scrappage Fraction](Mileage.md), which specifies the fraction of devices in any one vintage that can be scrapped, and the [Fraction of Scrapped Replaced](Fraction_of_Scrapped_Replaced.md) variable, which specifies the number of scrapped devices that should immediately be replaced with brand new devices at the same branch in the LEAP tree. When calculating scrappage, LEAP scraps the oldest vintages of devices first, subject to the [Max Scrappage Fraction](Max_Scrappage_Fraction.md), and progresses to scrap succeeding newer vehicles until the scrappage target has been reached or until there are no devices left to scrap. f the number specified in the scrappage variable is larger than the stock of devices then all devices will be scrapped (subject to the constraints of the Max Scrappage Fraction) and stocks for that year will be set to zero.  Any values for scrappage before the [First Sales Year](First_Sales_Year.md) will be ignored.