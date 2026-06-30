---
Source: https://leap.sei.org/help24/Expressions/StandardError.htm
---

# StandardError

## Syntax 1

StandardError(Year1, Value1, Year2, Value2,... YearN, ValueN)

Calculates the standard error for a time-series.  Standard error is a measure of an estimate's variability. The greater the standard error in relation to the size of the estimate, the less reliable the estimate. As a rough rule-of-thumb, one can be 95% confident that the true coefficient is within ±1.96 standard errors of the estimate, or 68% confident that the true coefficient is within ±1 standard error. Both year and value parameters may themselves be expressions referring to other branches and variables. The list must be specified in ascending chronological order. Accepts up to 400 year/value pairs.

## Syntax 2

StandardError([ExcelFile, ExcelRange](Excel_Ranges.md))

Calculates the standard error of the values specified in the Excel range.  The Excel range must be a year/value list consisting of both years and values. For more information see: [Specifying Excel file and range parameters](Excel_Ranges.md). Accepts up to 400 year/value pairs.

## Syntax 3

StandardError(Branch:Variable)

Calculates the standard error of the values contained in the referenced Branch/Variable. The referenced branch variable must itself be specified as a simple [Data](Data.md) or [Interp](Interp.md) function, such as Data(2020, 1, 2025, 2, 2030, 3).

## Syntax 4

StandardError(LCDS, Series Name, Filter1, Filter2, [CountryISO3])

Calculates the standard error of the values retrieved from the online [LEAP Cloud Data Server (LCDS)](../01%20-%20Introduction/LCDS__The_LEAP_Cloud_Data_Server.md). Retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.

## Example

StandardError(2010, 1, 2011, 2.5, 2012, 3, 2013, 4, 2014, 6, 2020, 20)   = 1.412