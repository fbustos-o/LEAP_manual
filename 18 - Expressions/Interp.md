---
Source: https://leap.sei.org/help24/Expressions/Interp.htm
---

# Interp

## Syntax

Interp(Year1, Value1, Year2, Value2,... YearN, ValueN, [ Growthrate])   
Interp([ExcelFile, ExcelRange](Excel_Ranges.md), [ Growthrate])  
Interp(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])  
Interp(Branch:Variable)

## Summary

Calculates a value in any given year by linear interpolation of a time-series of year/value pairs.  The final optional parameter to the function is a growth rate that is applied after the last specified year. If no growth rate is specified zero growth is assumed (i.e. values are not extrapolated). Each intermediate year's value is calculated as follows:

![](../assets/images/Expressions/Interp.gif)

Where:

iy = the intermediate period, the value of which is to be interpolated.  
ey = the end period used as the basis for the interpolation.  
fy = the first period used as the basis for the interpolation.

The second syntax of the function retrieves years and values from a [specified Excel file](Excel_Ranges.md) and range. The third syntax of the function retrieves years and values from the online [LEAP Cloud Data Server (LCDS)](https://leap.sei.org/data). In both cases, retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.  Use the [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to help specify the parameters required when using these syntax.

## Example

Interp(2000, 10.0, 2010, 16.0, 2020, 30.0, 2%)

2000 = 10.0  
2005 = 13.0  
2020 = 30.0  
2021 = 30.6

NB: the base yearThe first historical year of a LEAP analysis. value is always implicit in the above function, and will override any value explicitly entered for that year by the user. For example, if the base year is 1998 and the base year value (entered in Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year. ) is 6.0 then the function above will result in the value 8.0 1999.