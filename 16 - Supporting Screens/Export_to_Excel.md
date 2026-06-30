---
Source: https://leap.sei.org/help24/Supporting_Screens/Export_to_Excel.htm
---

# Export to Excel

Menu Option: Analysis: Export to Excel  
See also: [Import to Excel](ImportFromExcel.md)

![](../assets/images/NewScreens/Export2Excel.png)

Use this option to export to Excel all of the data in LEAP associated with the main tree structure.  That is, all of the data specified using expressions on LEAP's main screen.    This option will not export subsidiary databases such as the [Fuel](Fuels.md), [Effects](Effects_Screen.md) and [Units](Units.md) databases.  These databases can be exported from their own data entry screens.

This option is also used to set-up a blank template spreadsheet in preparation for importing data into Excel. For more information, see [Import to Excel.](ImportFromExcel.md)   

You can export data for:

* The current branch in the tree, the current branch and all branches below it, or all branches.
* The current scenario or all scenarios.
* The current variable or all variables.
* The current region or all regions.

By default LEAP will export all of its data to Excel.  Two other options let you set:

* Data to Export: This option lets you either export all data, or only data that is not inherited i.e. is explicitly entered) for a given scenario and region.
* Format:  you can choose to export LEAP's expressions to a single Excel column, or you can export the times series data values into multiple Excel spreadsheet columns.  One column will be exported for each of the default years that you specified  in the General [Settings](Basic_Parameters_Screen.md#Years): Years screen.  The first option is for directly editing expressions in Excel, the second is most useful for exporting data or for setting-up a template as the basis for importing data into Excel.

Sorting and Filtering of Branches: In addition to always exporting the full branch path for each branch, LEAP also allows you to optionally export each level of branch names as a separate column for easing sorting and filtering.  Use the levels spin button to specify how many separate level columns should be created in the sheet (minimum 0, maximum 10). LEAP can also optionally enable Excel's auto-filtering feature, to help you quickly sort through and filter the resulting spreadsheet.  If you don't want Excel to auto-filter the resulting spreadsheet, uncheck the Autofilter check box.

Once you have set these options, click OK to export to Excel, or Cancel to abort the export operation.