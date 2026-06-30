---
Source: https://leap.sei.org/help24/Supporting_Screens/Regions.htm
---

# Regions

Menu Option: General: Regions (also shown on the [main toolbar](../03%20-%20Interface/Main_Toolbar.md))  
See Also: [Region Groupings](Region_Groupings.md), [Maps](../02%20-%20Views/Maps.md)

![](../assets/images/NewScreens/Regions.png)

## Introduction

LEAP allows you to specify multiple regions within an area.  So for example, if you are doing a regional analysis then each region might be one country, if you are doing a global analysis (as shown above) then each region might be a collection of countries, or if you are doing a country-level analysis then each region might be a different state or province.

## Columns in the Regions Screen

* **Region Name:** If you have specified that your area is a multi-national application (on the [Settings](Basic_Parameters_Screen.md#Scope) screen) then the Regions screen will assist you as you type in the region names by suggesting the predefined names of known countries and auto-completing the abbreviation column based on each country's two letter (Alpha 2) ISO Code.  Alternatively, you can add or edit a region name by selecting from a pull-down list of known country names.  In addition, if you are using the [IBC Impacts Calculator](../12%20-%20The%20Impact%20Benefits%20Calculator%20%28IBC)/Introduction_to_IBC.md) extension, then an additional read-only column will be displayed indicating whether IBC currently supports each selected country. This column is marked "Works with IBC".
* **Grouping:** Each region is a separate data dimension, so you can specify different data for each region and view results either for one region or summed across regions. The [Region Groupings](Region_Groupings.md) screen lets you specify up to four named groups of regions for the purposes of reporting results aggregated across regions in the [Energy Balance](../02%20-%20Views/Energy_Balance_View.md) and [Results](../02%20-%20Views/Results_Screen.md) views.  So for example, if you create a global analysis, you could specify each region as a country and then specify regional groupings for Europe, North America, Africa, Latin America, Asia, etc. The region grouping features are optional.  If your data set contains only one region (which is true of any data set created in older versions of LEAP), then regional dimensions will not appear in the results or energy balance reporting views.

* **Inherit Expressions from Region:** In addition to allowing you to enter different data for each region, the regions feature also allows regions to inherit [expressions](../01%20-%20Introduction/Expressions.md) from one region to another for a given branch/variable/scenario expression.  So for example, you might specify that region "South" inherits expressions from region "North".  In this case you only need to enter data for region South where it differs from region North.  This can greatly simplify data entry and model management.  In the example shown above each region inherits its expressions from a region named "template".

* **Calculated:** Use this column to indicate which regions are calculated. In the example shown above, all regions except the "template" region are calculated.
* **Calculate IBC:** In multi-region areas set up to use [IBC: The Impact Benefits Calculator](../12%20-%20The%20Impact%20Benefits%20Calculator%20%28IBC)/Introduction_to_IBC.md), use the **Calculate IBC** column to indicate which regions will also have impact results calculated using IBC.  You can only edit fields in this column if the read only field **Works with IBC** is checked on. Note that in multi-region areas, IBC can only be used if the scale of the area is set to be global or multi-national. This is set on the [Settings: Scope](Basic_Parameters_Screen.md#Scope) screen.

## Using the Regions Screen

Click the ![](../assets/images/NewButtons/Add.png) button to add a new region.  Click the **![](../assets/images/NewButtons/Delete.png)** button to delete a region.  Bear in mind that this will erase all of the data associated with a region.  Click the **![](../assets/images/NewButtons/Arrow-up.png)** and **![](../assets/images/NewButtons/Arrow-down.png)** buttons to change the display ordering of regions.

When editing an area marked as a Global or Multi-national data set (via the [Scope & Scale](Basic_Parameters_Screen.md#Scope) tab on the Settings screen), you can make use of a pull-down list of predefined country names to help you fill the first region name column.  When you select one of the predefined country names, LEAP will automatically fill the Abbreviation column with the standard two-letter code for that country.  You can manually override these names.  In Global and Multi-national areas, an additional read-only column will also be displayed with check marks indicating whether the country you selected is currently set up to work with the [Impact Benefits Calculator](../12%20-%20The%20Impact%20Benefits%20Calculator%20%28IBC)/Introduction_to_IBC.md) extension (IBC). You cannot edit this data - it is provided only to give you feedback on whether your area can be used in conjunction with IBC.

You can sort the table by name, abbreviation or grouping by clicking on the appropriate column title.  A sort indicator is displayed in the column title to show which column is used to sort the table. The indicator shows the sort order using a triangle pointing up for ascending or down for descending sorts.

To rename a region, simply edit its name.  Click the **![](../assets/images/NewButtons/MS-Excel.png)** button to export the regions table to Microsoft Excel.  Click the ditto button (**![](../assets/images/NewButtons/Ditto.png)**) to duplicate a field value from the value immediately above it.

## Connecting LEAP to a GIS Shape File

In addition to using charts and tables to display results, in multi-region data sets you can also optionally display LEAP results on a color code GIS (Geographical Information System) map.

Maps are only available if certain conditions are met:

1. You are working on a multi-region area (i.e. one with more than one region).
2. You have chosen a GIS "shape" file in the General: [Settings](Basic_Parameters_Screen.md): Mapping screen.

If the above conditions are met, an additional column of data will be displayed in the Regions screen with which you can map each region in your area to a shape in the selected GIS shape file.  Each LEAP region can be mapped to one and only one GIS shape, so you will need to choose a GIS shape file that has the same level of regional disaggregation as your LEAP area.

Use the Guess Blank GIS Mappings button at the foot of the Regions screen to have LEAP attempt to guess the LEAP-to-Shape File mappings by matching the names used in LEAP to those used in the GIS shape file.

Once you have linked your regions to a shape file in this way, you can then display results in various types of maps in the Results View.  These maps are selected as additional chart types in the [Results View](../02%20-%20Views/Results_Screen.md).