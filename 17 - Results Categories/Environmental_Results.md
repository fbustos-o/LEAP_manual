---
Source: https://leap.sei.org/help24/Results_Categories/Environmental_Results.htm
---

# Environmental Results

See
also: [Results
View](../02%20-%20Views/Results_Screen.md)  
Result Type: Environment

You can display
results for any of the [effects](../16%20-%20Supporting%20Screens/Effects_Screen.md)
for which you have specified environmental loadings in your tree branch
structure.  Results can be shown organized by branch, effect, fuel,
scenario, year and region (in multi-regional areas).  Environmental
effect results are only available if you have checked "Energy Sector
Effect Loadings" in the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md):
Scope & Scale screen.  Non-energy sector effects are also available
if you check "Energy Sector Effect Loadings" in the same screen.

In addition
to specifying results for an individual effect, you can also show the
combined global warming potential (GWP) of one or more greenhouse gases
(GHGs).  GWP results can be shown measured in terms of the equivalent
amount of Carbon (C) or Carbon Dioxide (CO2).
Reports measured in terms of CO2
are a factor of 44/12 larger than those measured in terms of carbon. The
global warming potentials of each pollutant can be edited on the General:[Effects screen](../16%20-%20Supporting%20Screens/Effects_Screen.md) and default to the standard values
recommended for 100-years integration by the Intergovernmental Panel on
Climate Change (IPCC). For GWP reports you can choose between 20, 100
year and 500 year time horizons. Based on the time horizon you select,
LEAP uses different sets of global warming potentials for the non-CO2
gases that reflect the relative potential of the gas over each period.
Since GWP factors are always expressed relative to carbon dioxide, the
GWP of Carbon Dioxide is set to 1.0 for every time horizon. The default
GWP factors correspond to those recommended by the IPCC in its [Second
Assessment Report](https://www.ipcc.ch/pdf/climate-changes-1995/ipcc-2nd-assessment/2nd-assessment-en.pdf) (ARII).  However, you can manually edit these
default values in the General:[Effects](../16%20-%20Supporting%20Screens/Effects_Screen.md) screen,
or you can switch among whole sets of GWP factors corresponding to the
first, second, third and fourth IPCC assessment reports.

When viewing
environmental loadings, results are available in four different formats:

* Individual
  effects:  In this format effects are reported in their
  standard physical units as specified on the General: Effects screen.
    Note that these effects can include emissions as well
  as any other direct impacts.
* Direct
  GHG Emissions (at Point of Emissions):  This result shows
  direct GHG emissions at the point where emissions are produced in
  20, 100 and 500-year GWP values.  These emissions are shown at
  the demand, transformation and non-energy sector branches corresponding
  to where the emissions were produced (either through combustion or
  some sort of fugitive emission).  They may also include sinks
  (negative emissions).
* Direct
  (Demand) plus Indirect (Transformation) GHG Emissions Allocated to
  Demand Branches:  This result shows100-year GWP values
  for direct emissions from demand branches plus the indirect Transformation
  emissions associated with those demand branches.  This result
  type does NOT include GHG emissions specified under the non-energy
  sector branches in LEAP.
* Indirect
  (Transformation) GHG Emissions Allocated to Demand Branches:
   This result shows 100-year GWP values for indirect (Transformation)
  emissions associated with particular demand branches.  This result
  type does NOT include GHG emissions specified under the non-energy
  sector branches in LEAP.

Note that only the first two
result types are shown by default.  If you want to see the second
two result types go to the General: [Results to Save
Screen](../16%20-%20Supporting%20Screens/Result_Variables_to_Save.md) and enable those additional result types.  Bear in mind
that the more results you enable the slower calculations will become.

For all of these types
of environmental results, LEAP uses a territorial accounting approach
similar to the conventions used by the IPCC and UNFCCC for National GHG
Emissions Inventory Guidelines.  This approach accounts for fugitive
and combustion emissions that occur within the boundaries of a LEAP area
including emissions that were caused by energy sector operations that
resulted in a final fuel being exported (e.g. operations of power plants
or refineries within a country).  It excludes emissions that ultimately
occur when a country exports a primary fuel that is consumed in another
area.