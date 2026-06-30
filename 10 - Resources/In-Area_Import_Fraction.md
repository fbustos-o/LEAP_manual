---
Source: https://leap.sei.org/help24/Resources/In-Area_Import_Fraction.htm
---

# In-Area Import Fraction

See also: [In-Area Export Fraction](In-Area_Export_Fraction.md), [Regional Import Fraction](../08%20-%20Transformation/Regional_Import_Fraction.md)

(%) Fraction of the imports to this region coming from all other regions within this area. The remaining fraction comes from outside the area.

This variable is only visible for multi-region areas.  Its values should be between 0% and 100% but need not sum to any particular value across regions. The variable is only visible (and used in calculations) when you first enable Allow Trade Among Regions:
an option on the Calculation tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Calculations) scree.  You will also need to edit the [Fuels](../16%20-%20Supporting%20Screens/Fuels.md) screen and specify which resources can be trade among regions.

This variable is used to determine where the imports in any given region come from: either from somewhere within the area (i.e. another region in a multi-region area) or from beyond the area.  So for example, if "region Y" imports 500 PJ of
electricity, and 80% comes from its immediate neighbors (other regions in the Area) then you would enter the value 80 for region X in the In-Area Import fraction variable.  Think of this variable as creating the demand for in-area imports.  It works
in conjunction with the [In-Area Export Fraction](In-Area_Export_Fraction.md) variable, which then assigns responsibility to each area for producing exports to meet these import demands.

There are two basic methods of specifying trade among the regions in a LEAP area.

* Method 1 uses the [Regional Import Fraction](../08%20-%20Transformation/Regional_Import_Fraction.md) variable  (described above) to directly specify imports among specific regions for each output fuel of each module.
* Method 2 allows you to specify values for the [In-Area Import Fraction](In-Area_Import_Fraction.md) and [In-Area Export Fraction](In-Area_Export_Fraction.md) variables under the Resources branches.  This approach first calculates
  overall import requirements for each fuel in each given area. Next, it species what fraction of those imports are met within the area (as opposed to beyond the area) using the In-Area Import Fraction variable.
  Finally it uses the In-Area Export Fraction variable to specify which of the regions meet those in-area requirements.