---
Source: https://leap.sei.org/help24/Expressions/Step.htm
---

# Step

## Syntax

Step(Year1, Value1, Year2, Value2,... YearN, ValueN)   
Step(ExcelFilename, ExcelRangeName)  
Step(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])  
Step(Branch:Variable)

## See Also

[Using Time-Series Functions](Using_Time_Series_Functions.md), [Interp](Interp.md)

## Summary

Calculates a value in any given year using a step function between a time-series of year/value pairs.

The second syntax of the function retrieves years and values from a [specified Excel file](Excel_Ranges.md) and range. The third syntax of the function retrieves years and values from the online [LEAP Cloud Data Server (LCDS)](https://leap.sei.org/data). In both cases, retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.  Use the [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to help specify the parameters required when using these syntax.

## Examples

Step (2000, 300.0, 2010, 500.0, 2020, 900.0)

2000 = 300.0  
2012 = 500.0  
2022 = 900.0

NB: The base yearThe first historical year of a LEAP analysis. value is always implicit in the function, and will override any value explicitly entered for that year by the user. For example, if the base year is 1997 and the base year value (entered in Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year. ) is 200.0 then the function above will results in the value 200.0 for both 1998 and 1999.