---
Source: https://leap.sei.org/help24/Transformation/Minimum_Utilization.htm
---

# Minimum Utilization (%)

See
also: [Analysis
View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md),
[Maximum Availability](Maxiumum_Capacity_Factor.md)

This time-sliced variable, used primarily
in optimization calculations, puts a lower limit on the utilization of
processes.   In simulation modes, the variable is only used
to check that calculated dispatch values meet a specified minimum utilization
level.  If they do not an error is reported. In optimization calculations,
it acts as a constraint in the optimal dispatch calculations.  Minimum
utilization values must be less than or equal to [Maximum
Availability](Maxiumum_Capacity_Factor.md) values.

Minimum Utilization is only shown when you
have specified that a [Transformation
module's properties](Module_Properties_Wiziard.md) include capacity data.

Minimum Utilization is defined for each time
slice in a year.  If you don't expect minimum utilization to vary
within a year then you can enter a single value (between 0 and 100%).
 If it does vary (e.g. by season) then you can use the [YearlyShape
function](../18%20-%20Expressions/YearlyShape.md) to link to one of the library of [YearlyShapes](../16%20-%20Supporting%20Screens/Load_Shapes.md)
defined in your area.  Make sure you choose one of the YearlyShapes
that explicitly contains an availability profile.