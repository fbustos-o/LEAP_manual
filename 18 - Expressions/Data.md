---
Source: https://leap.sei.org/help24/Expressions/Data.htm
---

# Data

## Syntax

Data(Year1, Value1, Year2, Value2,... YearN, ValueN)   
Data([ExcelFile, ExcelRange](Excel_Ranges.md)),   
Data(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])  
Data(Branch:Variable)

## See also

[Using Time-Series Functions](Using_Time_Series_Functions.md) and [Specifying Excel File and Range Parameters](Excel_Ranges.md), [InterpFSY](InterpFSY.md)

## Summary

Specifies time-series data values as year/value pairs.  Values are not interpolated between data points.  Any unspecified data years are assumed to have zero value.

Typically you will use this function to specify historical data in the Current Accounts scenario. Data specified in this fashion can also be referred to by other time-series functions.  For example, you might specify time-series once in a key assumption branch called TimeValues using the Data function, and then refer to it in other branches as Interp(Key\TimeValues).

The second syntax of the function retrieves years and values from a [specified Excel file](Excel_Ranges.md) and range. The third syntax of the function retrieves years and values from the online [LEAP Cloud Data Server (LCDS)](https://leap.sei.org/data). In both cases, retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.  Use the [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to help specify the parameters required when using these syntax.

## Example

Data(2000, 10, 2001, 16, 2003, 20)

2000 = 10  
2001 = 16  
2002 =   0  
2003 = 20