---
Source: https://leap.sei.org/help24/Transformation/Has_Regional_Imports.htm
---

# Has Regional Imports

See also: [Regional Import Fraction](Regional_Import_Fraction.md), [In-Area Import Fraction](../10%20-%20Resources/In-Area_Import_Fraction.md),[In-Area Export Fraction](../10%20-%20Resources/In-Area_Export_Fraction.md)

This variable is a Yes/No switch used to indicate whether you wish to specify regional import fractions for a given output fuel.  It is only visible when editing multi regional data sets (data sets with more than one region) and it may only be edited for the first region in each area and when editing the Current Accounts data set.  In other words it is constant across all regions and all scenarios.  In addition, this variable is only visible when you enable Allow Trade Among Regions: an option on the Calculation tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Calculations) screen.

If set to "Yes", an extra set of branches will appear in the tree under the specified output fuel labeled "Imports from [Region]" for each calculated region marked with the Import icon (![](../assets/images/NewButtons/Arrow-right.png)).  At each of these branches you can set the Regional Import Fraction Variable, which specifies the fraction of requirements for the Output fuel at the module that are imported from other regions within the area.

There are two basic methods of specifying trade among the regions in a LEAP area.

* Method 1 uses the [Regional Import Fraction](Regional_Import_Fraction.md) variable  (described above) to directly specify imports among specific regions for each output fuel of each module.
* Method 2 allows you to specify values for the [In-Area Import Fraction](../10%20-%20Resources/In-Area_Import_Fraction.md) and [In-Area Export Fraction](../10%20-%20Resources/In-Area_Export_Fraction.md) variables under the Resources branches.  This approach first calculates overall import requirements for each fuel in each given area. Next, it species what fraction of those imports are met within the area (as opposed to beyond the area) using the In-Area Import Fraction variable. Finally it uses the In-Area Export Fraction variable to specify which of the regions meet those in-area requirements.