---
Source: https://leap.sei.org/help24/Resources/In-Area_Export_Fraction.htm
---

# In-Area Export Fraction

See also: [In-Area Import Fraction](In-Area_Import_Fraction.md). [Regional Import Fraction](../08%20-%20Transformation/Regional_Import_Fraction.md)

(%) Fraction of total in-area trade in a fuel met by exports from the selected region.

This variable is only visible in multi-region areas.  Its values should be between 0% and 100%, and should sum to 100% across all regions for each fuel. In addition, it is only visible when you enable Allow Trade Among Regions:
an option on the Calculation tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Calculations) screen. You will also need to edit the [Fuels](../16%20-%20Supporting%20Screens/Fuels.md) screen and specify which resources can be trade among regions.

This variable works in conjunction with the In-Area Import Fraction variable which creates a demand for internal trade within a multi-region Area.  Once this internal trade has been calculated the In-Area Export Fraction is used to specify which of
the regions meet that demand by exporting fuels to other regions in the area.