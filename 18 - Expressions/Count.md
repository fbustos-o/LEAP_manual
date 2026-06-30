---
Source: https://leap.sei.org/help24/Expressions/Count.htm
---

# Count

## Syntax 1

Count(Expression1, Expression2, ... ExpressionN)

Calculates the number of parameter values. Accepts up to 250 parameters. Parameters may themselves be expressions referring to other branches and variables.

[Observations](Observations.md) can also be used as an alias for Count.

## Syntax 2

Count(Year1, Value1, Year2, Value2,... YearN, ValueN)

Calculates the number of year/value pairs (observations) in the year/value list. Both year and value parameters may themselves be expressions referring to other branches and variables. The list must be specified in ascending chronological order. Accepts up to 400 year/value pairs.

## Syntax 3

Count([ExcelFile, ExcelRange](Excel_Ranges.md))

Calculates the number of year/value pairs specified in the Excel range. The Excel range must be a year/value list consisting of both years and values. For more information see: [Specifying Excel file and range parameters](Excel_Ranges.md). Accepts up to 400 year/value pairs.

## Syntax 4

Count(Branch:Variable)

Calculates the number of year/value pairs contained in the referenced Branch/Variable. The referenced branch variable must itself be specified as a simple [Data](Data.md) or [Interp](Interp.md) function, such as Data(2020, 1, 2025, 2, 2030, 3).

## Syntax 5

Count(LCDS, Series Name, Filter1, Filter2, [CountryISO3])

Calculates the number of year/value pairs retrieved from the online [LEAP Cloud Data Server (LCDS)](../01%20-%20Introduction/LCDS__The_LEAP_Cloud_Data_Server.md). Retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.