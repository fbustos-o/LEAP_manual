---
Source: https://leap.sei.org/help24/Land-based_Resource_Calculations/Visibility_of_Land-Based_Resource_Variables.htm
---

# Setting Up a Land-Based Resource Analysis in LEAP

See also: [Analysis View](../02%20-%20Views/Data_View.md),
[Land-based
Resource Calculations](../08%20-%20Transformation/Transformation.md)

Land-based resource calculations are optional, and by default are disabled
in the sample LEAP data set (Freedonia). There are a number of basic steps
required to set up a land-based resource analysis in LEAP.

1. First, go
   to the [Scope &
   Scale](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) tab of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md)
   screen and enable the option marked Land-Use
   Change and Land-Based Resources. Without doing that all variables
   related to land-based resource analysis will be hidden and excluded
   from LEAP's calculations.  Later on,  you can show or hide
   these capabilities as you wish.  Hiding these capabilities does
   not delete any data: it simply hides the data and excludes it from
   LEAP's calculations.
2. Next, you will
   need to create a list of land types for your analysis by visiting
   the General: [Land
   Types](../16%20-%20Supporting%20Screens/Land_Types.md) screen (also visible on the main tool bar in Analysis View).
3. Bear in mind
   also that land-based resource analyses typically require a geographically
   disaggregated analysis, so we strongly recommend basing your analysis
   on a multi-regional model of any sizable energy system (e.g. a country).
    Thus, you may also need to create a list of regions in your
   area.  You can do that by visiting the General: [Regions](../16%20-%20Supporting%20Screens/Regions.md)
   screen.
4. Next, you will need
   to set the Properties of any resources for which you wish to conducted
   a disaggregated land-based resource assessment.  To do this,
   you can edit the [properties
   of individual resources](../10%20-%20Resources/Resource_Properties.md), or by editing the By
   Land Type property in the General: [Fuels](../16%20-%20Supporting%20Screens/Fuels.md)
   screen.  You can use this type of analysis for wood fuels as
   well as for any type of geographically disbursed renewable energy
   forms including solar, wind and biomass.

Once you have followed the above steps, you will see an additional set
of branches in the main tree.  A new set of branches are shown under
the high level Land Areas branch.
 These contain variables (tabs) under which you can specify base
year land areas for each land type and future land conversions in each
scenario.  In addition, you will see a new set of branches, one for
each land type, under the Resources
high level branch, for those resources for which you have chosen to conduct
a disaggregated land-based resource analysis.

Notice that the set of variables (tabs) you will see under the Resources
branches, will depend on the type of fuel being studied.  When studying
wood resources you will see a large number of variables since LEAP considers
many issues such as the stocks and growth of wood, as well as the interactions
between the demand for wood and the various potential wood fuel supply
sources.  When dealing with other resources, LEAP only considers
annual energy productivity, not detailed wood demand/supply interactions.