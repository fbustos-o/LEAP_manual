---
Source: https://leap.sei.org/help24/Transformation/Regional_Import_Fraction.htm
---

# Regional Import Fraction

See
also: [Has Regional Imports](Has_Regional_Imports.md),
[In-Area Import Fraction](../10%20-%20Resources/In-Area_Import_Fraction.md),
[In-Area Export Fraction](../10%20-%20Resources/In-Area_Export_Fraction.md)

This variable specifies the percentage fraction
of requirements for an Output fuel of a module that is imported from each
other region within the Area.  It is only visible when editing multi
regional data sets  and when the Has [Regional
Imports](Has_Regional_Imports.md) variable is set to Yes
. In addition, this variable is only visible when you enable Allow
Trade Among Regions: an option on the Calculation
tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Calculations)
screen.

Regional Import Fractions are specified as
the percentage of requirements for each output fuel in a region met by
imports from each other region in the area.  Each value must be in
the range 0-100% and values must sum to less than or equal to 100% across
all regions.

There are two basic methods of specifying
trade among the regions in a LEAP area.

* Method 1 uses the Regional Import
  Fraction variable  (described above) to directly specify imports
  among specific regions for each output fuel of each module.
* Method 2 allows you to specify values
  for the [In-Area
  Import Fraction](../10%20-%20Resources/In-Area_Import_Fraction.md) and [In-Area
  Export Fraction](../10%20-%20Resources/In-Area_Export_Fraction.md) variables under the Resources branches.  This
  approach first calculates overall import requirements for each fuel
  in each given area. Next, it species what fraction of those imports
  are met within the area (as opposed to beyond the area) using the
  In-Area Import Fraction variable.
  Finally it uses the In-Area Export
  Fraction variable to specify which of the regions meet those
  in-area requirements.