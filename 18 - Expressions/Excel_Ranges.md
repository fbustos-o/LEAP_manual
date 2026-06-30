---
Source: https://leap.sei.org/help24/Expressions/Excel_Ranges.htm
---

# Specifying Excel File and Range Parameters

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Expressions](../01%20-%20Introduction/Expressions.md), [Using Time-Series Functions](Using_Time_Series_Functions.md)

When creating LEAP time-series functions such as [Interp](Interp.md) and [Step](Step.md), you can choose to pass data to the function from an Excel spreadsheet by specifying two or three parameters, the Excel file name and one or two parameters specifying the Excel range containing the data.    For example, you might write the following:

INTERP(MyModel.xls, B2:B27)

Excel file names must refer to an excel spreadsheet (a file with a ".xls" extension) that exists somewhere on your PC.  If you specify the file name only with no folders then LEAP will look for the file in the current Area folder.  In general it is good practice to store supporting spreadsheets in the LEAP area folder so that when you back-up a folder, or send it to another LEAP user the Excel sheets will stay with the other LEAP data files.  Spreadsheets located outside of the Area folder should be specified as fully qualified path names.

Time-series functions in LEAP require a data series consisting of pairs of years and data values.  Thus, the Excel ranges you refer to must also contain pairs of years and data values.  Valid ranges may be laid out in the following four ways:

1. A single contiguous range that is two cells wide with the first column containing the years and the second column containing the data.  These types of ranges can be specified as a single parameter.  For example, B2:C15.
2. A single contiguous range that is two cells high with the first row containing the years and the second row containing the data.  These types of ranges can be specified as a single parameter.  For example, B2:S3.
3. Two separate columns, each one cell wide,  passed as two parameters. The first parameter should contain the years and the second should contain the data.  For example: B2:B15, E2:15.
4. Two separate rows, each one cell high,  passed as two parameters. The first parameter should contain the years and the second should contain the data.  For example: B2:S2, B15:S15.

Note that the last two ways require passing three parameters in total: the filename and two range parameters.  Both ranges must have equal dimensions.  Using two parameters can be useful if your Excel spreadsheet is structured in a typical data table layout in such a way that the years and the values are not right next to each other.Note that in all cases, data must be organized in chronological order (from left to right or from top to bottom). Duplicate years are not allowed, and years must be in the range 1900-2200.

Note when data in LEAP is stored as a link to an Excel spreadsheet using the above expressions, then LEAP will automatically re-import data whenever the Excel spreadsheet is edited and re-saved.  When working simultaneously in LEAP and Excel You can press LEAP's Refresh key (F9) to force the analysis view to be refreshed.