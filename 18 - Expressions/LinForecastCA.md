---
Source: https://leap.sei.org/help24/Expressions/LinForecastCA.htm
---

# LinForecastCA

## Syntax

LinForecastCA(Year1, Value1, Year2, Value2,... YearN, ValueN) or  
LinForecastCA([ExcelFile, ExcelRange](Excel_Ranges.md))  
LinForecastCA(LCDS, SeriesName, Filter1, Filter2, [CountryISO3])  
LinForecastCA(Branch:Variable)  
LinForecastCA(FirstYear, LastYear)

**See also:** [Using Time-Series Functions](Using_Time_Series_Functions.md) and [Specifying Excel File and Range Parameters](Excel_Ranges.md), [LinForecast](LinForecast.md).

## Summary

Forecasts future values based on a linear regression (y=mx+c) of historical data. 

This function replaces the previous LinForecastBY function.

The second syntax of the function retrieves years and values from a [specified Excel file](Excel_Ranges.md) and range. The third syntax of the function retrieves years and values from the online [LEAP Cloud Data Server (LCDS)](https://leap.sei.org/data). In both cases, retrieving this data initially may takes some time (typically a second or less depending on your internet connection), but thereafter values are cached locally for near-instant retrieval.  Use the [Time-Series wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) to help specify the parameters required when using these syntax.

## Summary

Linear forecasting is used to forecast future values based on a time-series of historical data. The new values are predicted using linear regression assuming a linear trend ( y = mx +c) where the Y term corresponds to the variable to be forecast and the X term is years. Linear forecasting is most suitable in cases where exponential growth in values is not expected: for example when forecasting how market shares or technology penetration rates might change over time.

Use this function with caution. You may need to first use a spreadsheet or some other package to test the statistical validity of the forecast (i.e. test how well the regression "fits" the historical data). You can also use the LEAP's built-in statistical functions such as [RSquared](RSquared.md), [StandardError](StandardError.md), and [Observations](Observations.md) to help with this task.  The [Time-series Wizard](../21.6%20-%20Wizards%20and%20Properties/Time_Series_Wizard.md) will also diplay these basic statsical parameters. Bear in mind that future values may be markedly different from historical ones, particular if structural or policy shifts in the economy such as changing energy policies are likely to have an impact on future trends.

Typically, you will enter this function in your Current Accounts data and use it to forecast values for the scenario period from the [FirstScenarioYear](FirstScenarioYear.md) onwards. The function will return actual data vales for the Current Accounts period. If you wish to use forecast values for the Current Accounts period use the [LinForecast](LinForecast.md) function.

The syntax LinForecastBY(FirstYear, LastYear) is a special syntax that can only be used in scenarios (not in Current Accounts).  This syntax generates a forecast in a scenario based on the data in Current Accounts.  Only the values between and including FirstYear and LastYear are used as input to the regression that generates the forecast.  FirstYear must be on or after the base year. LastYear must be before the first scenario year. LastYear must be at least three years after FirstYear.