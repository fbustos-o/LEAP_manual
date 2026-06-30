---
Source: https://leap.sei.org/help24/Expressions/Using_Time_Series_Functions.htm
---

# Using Time-Series Functions

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Expressions](../01%20-%20Introduction/Expressions.md), [Pasting Arrays of Numbers into LEAP](../16%20-%20Supporting%20Screens/Pasting_Arrays_of_Numbers.md)

LEAP supports various time series functions, which let you specify historical data, fill gaps in data using the [Interp](Interp.md), [Step](Step.md) and [Smooth](Smooth.md) functions and forecast future values using the [LinForecast](LinForecast.md), [ExpForecast](ExpForecast.md) and [LogisticForecast](LogisticForecast.md) methodologies.  Each of these functions need to be supplied with time-series data, consisting of pairs of year/value data and an optional percentage growth rate parameter, which is applied after the last data year.  Time-series data can be entered in different ways:

1. Typed directly into the function  
     
   Interp(Year1, Value1, Year2, Value2,... YearN, ValueN, [% Growthrate])
2. Retrieved from an MS-Excel spreadsheet  
   Interp(ExcelFile, ExcelRange, [% Growthrate])  
     
   See also: [Specifying Excel File and Range Parameters](Excel_Ranges.md)
3. **Retrieved from the LEAP Cloud Data Server (LCDS)**  
   Interp(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])  
   [More information on the LCDS here](https://leap.sei.org/data).
4. As a reference to data in another LEAP branch/variable.  The data in the referenced cell must be specified using the [Data](Data.md) function and must consist only of year/value time series pairs.

For example, suppose you had the following fuel price data recorded in a branch named Key Assumptions\Price:  
Data(1990, 110 1991, 105, 1992, 108, 1994, 112, 1995, 115, 1996, 109, 1997, 135, 1998, 150)

This data could then be referenced by any timer-series function through a reference to the branch, such as:  
Interp(Key\Price)

Use the LEAP [Time-series Wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to simplify entering time-series data and to specify links to Excel data.  When specifying time-series data, years should be in chronological order.  Duplicate years are not allowed, and years must be in the range 1900-2200.