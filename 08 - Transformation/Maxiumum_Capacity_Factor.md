---
Source: https://leap.sei.org/help24/Transformation/Maxiumum_Capacity_Factor.htm
---

# Maximum Availability (%)

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Minimum Utilization](Minimum_Utilization.md)

Use this time-sliced variable to put an upper limit on the availability of processes. The maximum availability of a process is the ratio of the maximum energy produced to what would have been produced if the process ran at full capacity for a given period (expressed as a percentage). Maximum availability is normally defined by planned and forced outages. It is entered along with capacity data, and the product of the two is the maximum available capacity in any [time slice](../16%20-%20Supporting%20Screens/Time_Slices.md).

Maximum Availability is only shown when you have specified that a [Transformation module's properties](Module_Properties_Wiziard.md) include capacity data.

Maximum Availability is defined for each time slice in a year.  If you don't expect availability to vary within a year then you can enter a single value (between 0 and 100%).  If maximum availability does vary (e.g. by season) then you can use the [YearlyShape function](../18%20-%20Expressions/YearlyShape.md) to link to one of the library of [YearlyShapes](../16%20-%20Supporting%20Screens/Load_Shapes.md) defined in your area.  Make sure you choose one of the yearly shapes that explicitly contains an availability profile.