---
Source: https://leap.sei.org/help24/Views/User-Created_Summary_Reports.htm
---

# User-Created Summary Reports

See also: [View Bar](View_Bar.md), [Summaries View](Cost_Summary_View.md), [Cost-Benefit Summary Reports](Cost_Summary_Report.md), [Decomposition Reports](Decomposition_Summary_Reports.md), [Marginal Abatement Cost Curve (MACC) Reports](Marginal_Abatement_Cost_Curve_%28MACC)_Reports.md)

Unlike results show in the [Results view](Results_Screen.md), which display the values of a single variable, user-created summary reports are able to show the results for multiple variables on a single chart or table.  This type of report can be created and displayed from the [Summaries View](Cost_Summary_View.md) screen in LEAP.

User-created summary reports consist of rows, each of which displays either a heading or one variable for a given branch in the tree and columns which can be configured to display years, scenarios and regions as the columns of the report.

Use the [Manage Summaries](../16%20-%20Supporting%20Screens/Manage_Summaries.md) screen to create a named user-created summary report. You can create as many of these reports as you like, each of which can show results for different variables. Use the following options to edit individual reports:

**![](../assets/images/NewButtons/Add.png)** Add: Click to add a new branch/variable combination as a row in the report. Use the [Branch/Variable selection wizard](../16%20-%20Supporting%20Screens/Branch_Variable_Picker.md) to specify the branch, variable, units, scaling factor and any special results filters for the each variable.

**![](../assets/images/NewButtons/Delete.png)** Delete: Click to delete the currently highlighted row of the report. Note that you will not be deleting any data, you will only be removing the row from the report.

**![](../assets/images/NewButtons/Properties.png)** Edit Click to edit the branch/variable in a row.

Heading: Click to insert either a blank row in the report, or to insert a subheading. You will be prompted to enter text for the heading. Leave this blank to enter a blank row. LEAP will automatically group the rows between headings.

**![](../assets/images/NewButtons/Arrow-up.png)** Up: Click to move the current row up.

**![](../assets/images/NewButtons/Arrow-down.png)** Down: Click to move the current row down.

Columns: Use the two Columns selection boxes to select all or selected years or scenarios as the rows of the report. Notice that only scenarios marked for calculation in the [Manage Scenarios](../16%20-%20Supporting%20Screens/Scenario_Manager.md) screen are available. When displaying years as columns, a further selection box will be displayed in which you select a scenario to be displayed in the report. Similarly, when scenarios are the columns, a further selection box will be displayed in which you select a year to be displayed in the report.

User-created summary reports can be displayed both as tables and as charts.  When showing in chart format, the format of the chart will depend on the whether columns used in the tabular report.  When showing results by region or scenario, the chart will display values in bar chart format.  When showing years, the chart will display values as a line chart, with values indexed to a base year value of 1.0.

Various on-screen options displayed in a tool bar on the right of the screen can be used to customize the display of the tables and charts. You can increase (**![](../assets/images/NewButtons/Decimal-increase.png)**) or decrease (**![](../assets/images/NewButtons/Decimal-decrease.png)**) the number of decimals displayed in the table, change the display of grid lines on the chart (**![](../assets/images/NewButtons/Grid-Both.png)**), change the table font (**![](../assets/images/NewButtons/Font.png)**), export tables to Excel (**![](../assets/images/NewButtons/MS-Excel.png)**), print tables and charts (**![](../assets/images/NewButtons/printer.png)**), copy charts and tables to the Windows clipboard (**![](../assets/images/NewButtons/Copy.png)**), and export charts to PowerPoint (**![](../assets/images/NewButtons/MS-Excel.png)**).