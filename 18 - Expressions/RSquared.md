---
Source: https://leap.sei.org/help24/Expressions/RSquared.htm
---

# RSquared

## Syntax 1

RSquared(Year1, Value1, Year2, Value2,... YearN, ValueN)

Calculates the R-Squared value for a time-series.  R-squared is a statistical measure of how well a regression approximates real data points (in this case how close the values are to increasingly linearly over time).  An r-squared of 1.0 indicates a perfect fit. Both year and value parameters may themselves be expressions referring to other branches and variables. The list must be specified in ascending chronological order. Accepts up to 400 year/value pairs.

The formula for r is:

r(X,Y)   =   Cov(X,Y) ] / [ StdDev(X) x StdDev(Y)

## Syntax 2

RSquared([ExcelFile, ExcelRange](Excel_Ranges.md))

Calculates the R-Squared of the values specified in the Excel range.  The Excel range must be a year/value list consisting of both years and values. For more information see: [Specifying Excel file and range parameters](Excel_Ranges.md). Accepts up to 400 year/value pairs.

## Syntax 3

RSquared(Branch:Variable)

Calculates the R-Squared of the values contained in the referenced Branch/Variable. The referenced branch variable must itself be specified as a simple [Data](Data.md) or [Interp](Interp.md) function, such as Data(2020, 1, 2025, 2, 2030, 3).

## Syntax 4

RSquared(LCDS, Series Name, Filter1, Filter2, [CountryISO3])

Calculates the R-Squared of the values retrieved from the online [LEAP Cloud Data Server (LCDS)](../01%20-%20Introduction/LCDS__The_LEAP_Cloud_Data_Server.md). Retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.

## Example

RSquared(2010, 2, 2012, 2, 2015, 4 ,2020, 6, 2023, 8, 2025, 8, 2030, 10, 2035, 12, 2040, 18)  = 0.9585