---
Source: https://leap.sei.org/help24/Transformation/Merit_Order.htm
---

# Merit Order

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md)

The Merit Order of a process indicates the order in which it will be dispatched.  The merit order variable is only shown when you have specified that a [Transformation module's properties](Module_Properties_Wiziard.md) include capacity data and system load curve data, and is only used in a dispatch simulation if the [Process Dispatch Rule](Process_Dispatch_Rules.md) is set to MeritOrderDispatch.

Processes with the lowest value merit order are dispatched first (base load) and those with the highest merit order are dispatched last (peak load). Processes with equal merit order are dispatched together in proportion to their available capacity (Capacity * Availability).

Merit order is defined for each [time slice](../16%20-%20Supporting%20Screens/Time_Slices.md) in a year.  This allows processes to be dispatched differently in different seasons of a year. For example, a hydro plant may be dispatched as base load (merit order = 1) in a wet season and as peak load in a dry season.  The General: [Time Slices](../16%20-%20Supporting%20Screens/Time_Slices.md) screen is used to view and edit how a year is divided into different time slices.   Merit order values can be input as simple numbers or as expressions, just like other LEAP variables.  If you don't expect availability to vary within a year then you can enter a single value (positive integer values).  If merit orders do vary (e.g. by season) then you can use the [YearlyShape function](../18%20-%20Expressions/YearlyShape.md) to link to one of the library of [YearlyShapes](../16%20-%20Supporting%20Screens/Load_Shapes.md) defined in your area.  Make sure you choose one of the YearlyShapes that explicitly contains a merit order profile.

Merit order is not used for processes marked as storage processes.