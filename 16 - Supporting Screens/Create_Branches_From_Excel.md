---
Source: https://leap.sei.org/help24/Supporting_Screens/Create_Branches_From_Excel.htm
---

# Create Branches From Excel

Menu Option: Tree: Create Branches from Excel

![](../assets/images/NewScreens/CreateBranches2.png)

Some of the data required for energy planning is often available in tabular form.  For example, you may be able to find a table containing many of the technical characteristics of the various power plants in your country.  Typically such a table would be organized so that the rows of the table contain the names of the power plants (or the names of types of power plants) while the columns would contain different types of data such as the efficiency, maximum availability, capital cost, lifetime and fixed and variable operating & maintenance costs, etc.

The Create Branches from Excel wizard provides a convenient way to take a table like this in Excel and then use it to create a set of branches in LEAP, while also importing all of the data in the table into LEAP's Current Accounts data set.  The wizard works by asking you to map the types of data in your spreadsheet table to the various variables expected by LEAP. Where possible the wizard will also help to converting the data in the spreadsheet into the measurement units expected in LEAP.

To use the wizard, first select a Transformation Processes branch, a Demand Category branch, a Key Assumption Category branch, or a non-energy sector category branch.  Next, right-click on that branch and select Create Branches from Excel.  Note that these branches should have no child branches below them.

On the first page of the resulting wizard you will need to select the table of data you want to import.  Do this by selecting the filename for the Excel Spreadsheet and then selecting the Range in the Excel worksheet that contains the data.  The easiest way to use this feature is to first mark the table in Excel by creating a named range of data that includes both the row names and column headers for the data you want to import and to leave that sheet open within Excel. The LEAP wizard should detect this data and automatically use it.  Next, you should also select the orientation of the table (i.e. whether the rows contain the names of the branches or whether the rows contain the types of data corresponding to the variables in LEAP).

When you press Next, LEAP will scan the data in Excel and then show a second page of the wizard.  At the top of this second page, you will see a summary of the branches that LEAP proposes to create.  Below that you will be asked to match up the types of data in Excel to the variables require in LEAP.  If the column name in Excel matches a variable named required in LEAP then LEAP will automatically match-up the column names and LEAP variable name.

Once you have mapped the columns (or rows) of data in Excel to the variables required in LEAP, press the **F**inish button (![](../assets/images/NewButtons/OK.png))and LEAP will create the indicated set of branches immediately below the current highlighted branch.  The names of these branches (versus the names used for each technology in Excel) will be automatically adjusted by to ensure they follow the branch naming rules in LEAP.  To abandon the process, click the Cancel button (![](../assets/images/NewButtons/Cancel.png)).  If you do not create any data mappings you can still use the wizard to create a new set of branches in LEAP, although no numeric data will be imported.

## Units Conversion

Where possible LEAP will also try to establish the correct factor required to convert the data in Excel into the units required in LEAP.  This factor is displayed in the wizard and you can override it where necessary.  To try and establish a factor, LEAP looks for a scaling factor and unit written within square brackets in the label for the data column in the Excel range.  For example, you may have a data column containing capacity data marked as "Capacity [Thousand KW]" (note the scale and units are expected to be written within square brackets). Assuming that you wish to import this into the Exogenous Capacity variable in LEAP,  LEAP will compare this unit in Excel to the capacity unit you are using in LEAP (which for example may be GW) and thereby suggest a conversion factor. If the text in the square brackets is missing or cannot be properly recognized, then LEAP will fall back to the default conversion factor of 1.0.

## Special Types of Data

In addition to letting you map the data columns in Excel to the variables needed in LEAP, the wizard will also try to make use of certain special columns of data containing information specific to particular types of technologies.  For demand and Transformation technologies the wizard will look for a column of data marked with the label "Fuel" or "Fuels" and if available will use the contents of the this column to associate particular fuels with the branches it creates.  Similarly, for non-energy sector branches, the wizard looks for a column of data marked with the label "Effect" or "Effects" and uses the contents of the this column to associate particular effects with the branches it creates.

In addition, if the wizard finds a column of data marked with the label "Tag" or "Tags" it will use the contents of that column to create a set of [tags](../15%20-%20Tagging%20Branches/Tagging_Branches.md) associated with each of the branches it creates.  The tags in the column are required to be labels separated by commas.

The screen shot below shows an example of the type of Excel table that can imported into LEAP using the Create Branches from Excel wizard.  Note in particular how the technology names are the rows of the table, while the column headings contain the types of data to be matched with LEAP's variable names.  Note also that the units of measurement for each type of data are specified in square brackets as part of the column header cell.  Finally, note how this table contains two special columns containing the Fuels and Tags to be created in LEAP.

![](../assets/images/NewScreens/ExampleExcelSheet.png)