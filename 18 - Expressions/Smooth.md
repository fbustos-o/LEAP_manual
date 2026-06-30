---
Source: https://leap.sei.org/help24/Expressions/Smooth.htm
---

# Smooth

## Syntax

Smooth (Year1, Value1, Year2, Value2,... YearN, ValueN) or  
Smooth ([ExcelFile, ExcelRange](Excel_Ranges.md))

Smooth(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])

## See Also

[Using Time-Series Functions](Using_Time_Series_Functions.md) and [Specifying Excel File and Range Parameters](Excel_Ranges.md)

## Summary

Estimates a value in any given intermediate year based on the year/value pairs specified in the function and a smooth curve polynomial function of the form

Y = a + b.X + c. X2 + d. X3 + e.X4 + ...

When more points are available, a higher degree polynomial is used to give a more accurate fit. A minimum of 3 year/value pairs are required in order for the curve to be estimated.

Using the above two alternatives syntax, year/value pairs can either be entered explicitly or linked to a range in an Excel spreadsheet. Use the Time-series Wizard to input these values or to specify the Excel data. In either case, years do not need to be in any particular order, but duplicate years are not allowed, and must be in the range 1990-2200.

When linking to a range in Excel, you must specify the directory and filename of a valid Excel worksheet or spreadsheet (an XLS or XLW) file, followed by a valid Excel range. A range can be either a valid named range (e.g. "Import") or a range address (e.g. "Sheet1!A1:B5"). Excel ranges must be structured in one of two ways:

1. * As 2 columns of data, in which the first column is years and the second is values, or
   * as 2 rows of data in which the first row is years and the second is values.
   * In either case, the data must be organized in chronological order (from left to right or from top to bottom).

NB: The base yearThe first historical year of a LEAP analysis. value is always implicit in the function, and will override any value explicitly entered for that year by the user.

The second syntax of the function retrieves years and values from a [specified Excel file](Excel_Ranges.md) and range. The third syntax of the function retrieves years and values from the online [LEAP Cloud Data Server (LCDS)](https://leap.sei.org/data). In both cases, retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.  Use the [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to help specify the parameters required when using these syntax.

## Tip

Use the Time-Series Wizard to enter the data for this function.