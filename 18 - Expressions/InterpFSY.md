---
Source: https://leap.sei.org/help24/Expressions/InterpFSY.htm
---

# InterpFSY

## Syntaxes

InterpFSY(Year1, Value1, Year2, Value2,... YearN, ValueN, [ Growthrate])   
InterpFSY([ExcelFile, ExcelRange](Excel_Ranges.md), [ Growthrate])  
InterpFSY(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])  
InterpFSY(Branch:Variable)

## See Also

[Using Time-Series Functions](Using_Time_Series_Functions.md) and [Specifying Excel File and Range Parameters](Excel_Ranges.md), [Interp](Interp.md).

## Summary

Calculates a value in any given year by linear interpolation of a time-series of year/value pairs. Similar to the [Interp](Interp.md) function, but with the following differences:

* In the standard [Interp](Interp.md) function, the base yearThe first historical year of a LEAP analysis. value is always an implicit interpolated value and will override any value explicitly entered for that year by the user.
* In the InterpFSY function, the year immediately before the First Scenario Year is the implicit interpolated value.

The Base Year and First Scenario Year are both defined on the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md): Years screen.

The second syntax of the function retrieves years and values from a [specified Excel file](Excel_Ranges.md) and range. The third syntax of the function retrieves years and values from the online [LEAP Cloud Data Server (LCDS)](https://leap.sei.org/data). In both cases, retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.  Use the [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to help specify the parameters required when using these syntax.