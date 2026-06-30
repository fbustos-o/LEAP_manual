---
Source: https://leap.sei.org/help24/Wizards_and_Properties/Time_Series_Wizard.htm
---

# Time-Series Wizard

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Expressions](../01%20-%20Introduction/Expressions.md), [Examples of Expressions](../02%20-%20Views/Examples_of_Expressions.md)

The Time-Series Wizard is a tool that helps you construct the various time-series expressions supported by LEAP's [Analysis View](../02%20-%20Views/Data_View.md). These expressions include functions for interpolation, step functions, smooth curves and linear, exponential and logistic projections.  The data for these functions can be entered manually by keyboard (![](../assets/images/NewButtons/Keyboard_64.png)), drawn from or linked to the cells in an Excel spreadsheet (![](../assets/images/NewButtons/MS-Excel.png)) or connected to [LCDS: the LEAP Cloud Database Server](../01%20-%20Introduction/LCDS__The_LEAP_Cloud_Data_Server.md) (![](../assets/images/NewButtons/cloud-download.png)). The wizard is divided into three pages, which you step through using the Next (![](../assets/images/NewButtons/Arrow-right.png)) and Previous (![](../assets/images/NewButtons/Arrow-left.png)) buttons.

## Page 1: Function

![](../assets/images/NewScreens/TSWizard1.png)

Use this page to select the type of function you want to create. The functions are summarized in graph form on screen as shown below, and are grouped into two main types. The functions on the top row allow you to specify data points for various future years, and the function then calculates the values for intervening years:

1. * The interpolation function calculates values based on a linear (straight line) interpolation between the values you specify.
   * The step function assumes that values change discretely at the specified data years. In other words, values stay constant after a specified data year, until the next specified data year.
   * The smooth curve function calculates a best-fit smooth curve based on a polynomial least-squares fit of the specified data points. To achieve a good fit, the smooth curve function requires at least 3 data points.

The interpolation and smooth curve functions are most useful when you expect data to change gradually (for example when modeling the gradual penetration of some common deviceA type of demand branch, which contains information about a fuel-using technology. such as refrigerators or vehicles). The step function is most useful for specifying "lumpy" changes to the energy system, such as the addition of specific power plants to an electric generation system.

The functions on the bottom row, allow you to specify historic data values (i.e. values before the base yearThe first historical year of a LEAP analysis.). The different functions are then used to extrapolate data forward to calculate future values. Extrapolations are based on linear, exponential or logistic least-squares curve fits. Use these functions with care. The onus is on you to ensure that the projections are reasonable, both in terms of how a) well the estimated curve fits the historical data, and b) how policies and other structural factors may change in the future. In other words, be sure to consider how well you can identify past trends, but also if it is reasonable to expect these past trends to continue into the future. LEAP helps you with task a) by providing various statistics describing the curve-fit: the R2 value, the standard error, and the number of observations. If you need to do a more detailed analysis, we suggest you use the data analysis features built-in to Microsoft Excel, and then link your results to your LEAP analysis (see below).

## Page 2: Data Source

![](../assets/images/NewScreens/TSWizard2.png)

On page 2 shown below, you select the source of the data for the expressionA mathematical formula used to specify how the values of a variable changes from year to year.. There are three choices:

**![](../assets/images/NewButtons/Keyboard_64.png) Keyboard:** That is, you will type in the data directly.

![](../assets/images/NewButtons/MS-Excel.png) Excel: Using this option you can either import the values from selected cells in an Excel spreadsheet or create a permanent link to the values in those cells.  In the latter case, your LEAP model will be automatically updated any time the linked Excel sheet is also saved after editing.

![](../assets/images/NewButtons/cloud-download.png) **LCDS: The LEAP Cloud Data Server:** With this option, you can bring data into LEAP from [LCDS: The LEAP Cloud Data Server](../01%20-%20Introduction/LCDS__The_LEAP_Cloud_Data_Server.md): an easy-to-use, internet-hosted database containing international open-source data covering energy, emissions, and development data.

## Page 3: Enter Data

![](../assets/images/NewScreens/TSWizard3.png)

#### Method 1: Entering Data from the Keyboard

****![](../assets/images/NewButtons/Keyboard_64.png)****Depending on you choice on page 2, in page 3 you either enter the data used by the function using the data table on the left-hand side of the wizard, or you select an Excel spreadsheet and range(s) from which to extract the data for the selected time-series function.  The data you is previewed on the right-hand side of the wizard both as a chart and also as the expression that will be used in LEAP.

1. When entering data directly, use the Add (![](../assets/images/NewButtons/Add.png)) and Delete (![](../assets/images/NewButtons/Delete.png)) buttons to add or delete new year/value pairs, or click and drag data points on the adjoining graph to edit values graphically. For the Interpolation function, an additional data field is shown allowing you to specify a percentage growth rate, which is applied after the last specified data year. By default this value is zero. In other words, by default values are not extrapolated past the last interpolation data year. The data you enter will be shown as the points on the preview chart, while the line drawn on the chart will reflect the projection method you are using.

   In Current Accounts, when creating a linear or exponential regression, an additional check box will be displayed giving you the option of forcing the regression curve through the base year value.

#### Method 2: Importing Data from Excel or Linking to Data in Excel

****![](../assets/images/NewButtons/MS-Excel.png)****When linking to a Microsoft Excel sheet, a slightly different screen will be displayed. On this screen, first enter the name of the worksheet file (.xls or .xlsx) or use "..." button to browse for the file. Next enter the range or ranges from which the data will be extracted, or click the button attached to the field to select from any named ranges in the worksheet. Ranges can be specified either as names, or as Excel range formulae (e.g. Sheet1!A1:B16).

When taking data from Excel, you can specify either a single range structured as 2 columns or 2 rows of data, in which the first column or row is years and the second column or row is values.  Alternatively you can specify two ranges each of which contains a single row or a single column of data.  In this case, the first range should contain years and the second range should contain values.  Some of the values may be blank reflecting missing data.  In all cases, the data must be organized in chronological order (from left to right or from top to bottom.  When specifying two ranges, both ranges must be of equal size (i.e. have the same number of rows or columns).

Click on the Get Excel Data button to extract the data from Excel and preview the values in the adjoining graph. The points on the chart will be the values in the Excel spreadsheet, while the line drawn on the chart will reflect the projection method you chose on page one. We suggest that you store any subsidiary Excel worksheets in the same folder as your LEAP area data (i.e. under the My Documents\LEAP Areas\Area Name folder). By using this approach, your Excel worksheets will be copied, backed-up and restored along with all the other area data.

Use the Create Expression As radio buttons to choose how the data should be inserted into the expression you are editing: either as a live Excel link, which will be updated whenever the spreadsheet is edited and saved, or as data, which is initially copied from Excel, but will not subsequently be updated if the Excel spreadsheet is changed. Creating links to Excel spreadsheets is a good approach if you wish to do most of your editing work in Excel, or if you wish to conduct additional modeling outside of LEAP. However, it will also slow down LEAP calculations.

Once you have selected an Excel worksheet and range, you can click on the large Excel button (![](../assets/images/NewButtons/MS-Excel.png)) to open a copy of Excel and preview the worksheet and range.

#### Method 3: Linking to Data in the LEAP Cloud Data Server (LCDS)

****![](../assets/images/NewButtons/cloud-download.png)****The LEAP [Cloud Database Server (LCDS)](../01%20-%20Introduction/LCDS__The_LEAP_Cloud_Data_Server.md) is an easy-to-use system for connecting LEAP models to an internet-hosted database containing international open-source data covering energy, emissions, and development topics.

When accessing data from the LCDS, you will first be asked to pick a particular data set such as the UN Population Prospects, UN energy statistics or World Bank World Development Indicators. Depending on the data set, you will then be asked to filters to access particular records within the data set.  For example, for the U.N. Population prospects, you can choose among the low, medium, or high projections, while for the U.N. energy statistics you can select particular "flow codes" corresponding to particular sectors of the economy or rows in an energy balance, and particular "product codes" (corresponding to different fuels or energy forms consumed or produced at those sectors. All of the data currently contained in the LCDS are national statistics. Therefore, as a final step, you will be asked to select the particular country whose statistics you want to retrieve.

You will not need to manually select a country if either of the following two conditions hold:

1. The LEAP area is specified as being national scale and you have already specified a country for your area on the Settings: [Scope](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) screen, or
2. The LEAP area is specified as being multi-national on the the Settings: [Scope](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) screen and you have mapped the regions of your area to particular countries in the [Regions](../16%20-%20Supporting%20Screens/Regions.md) screen.

![](../assets/images/NewScreens/LCDS1.png)

Once you have made chosen your data using the selection boxes on the left of the wizard, LEAP will retrieve that data from LCDS.  This normally takes a few seconds. The data retrieved from the LCDS is cached locally so that it can be accessed rapidly when needed in your model's calculations.

The results retrieved are shown on the right of the screen. LEAP displays a preview chart showing the data values and also gives presents a preview of the expression that will be inserted into your LEAP model in one of the tabs in the bottom-right of the wizard.  Other tabs show you the raw data retrieved (years and values) and the URL used to query the LCDS database.  Finally, the LCDS also returns a set of notes documenting the source of the returned data including its authors, and the date retrieved.  These notes are automatically added to the [notes](../03%20-%20Interface/Notes.md) for the branch where data from the LCDS is inserted into your model.