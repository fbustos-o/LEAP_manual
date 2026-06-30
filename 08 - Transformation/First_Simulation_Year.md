---
Source: https://leap.sei.org/help24/Transformation/First_Simulation_Year.htm
---

# First Simulation Year

See also: [Analysis
View](../02%20-%20Views/Data_View.md), [Transformation
Analysis](Transformation.md)

When
dispatching processes to try and meet the energy and power requirements
for each module, LEAP can operate in two different calculation modes as
follows:

1. Historical dispatch is used in each
   year before the [First
   Simulation Year](First_Simulation_Year.md).  In
   these years, LEAP runs each process up to the amount specified in
   the Historical Production tab.  If the amount specified in the
   Historical Production tab would cause the process to exceed its maximum
   available capacity, LEAP displays a diagnostic error message.
2. Simulation: From the [First Simulation Year](First_Simulation_Year.md)
   onwards, LEAP simulates dispatch using the [Dispatch
   Rule](Process_Dispatch_Rules.md) specified for each process.

## Tips

1. If
   you want dispatch to be simulated
   in ALL years (i.e. you want LEAP to never use Historical Production
   values) then set the First Simulation Year to a year before the base
   year.
2. Conversely,
   if you want LEAP to always use historical production values set the
   First Simulation Year to a year after the study end year.
3. This
   variable is set by default to the expression [FirstScenarioYear](../18%20-%20Expressions/FirstScenarioYear.md).
    In other words, simulation starts in the first scenario year.
    The First Scenario Year is set on the [Years](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Years)
   tab of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md)
   screen.