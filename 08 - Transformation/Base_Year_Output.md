---
Source: https://leap.sei.org/help24/Transformation/Base_Year_Output.htm
---

# Historical Production

See also: [Analysis
View](../02%20-%20Views/Data_View.md), [Transformation
Analysis](Transformation.md)

This
variable specifies annual energy production (output) for a process,  You
can set the scale and units used to measure the variable in each module.

When
dispatching processes to try and meet the energy and power requirements
for each module, LEAP can operate in two different modes as follows:

* Historical dispatch is used in each
  year before the [first simulation
  year](First_Simulation_Year.md).  In these years,
  LEAP simply runs each process up the amount specified in the Historical
  Production tab.  If the amount specified in the Historical Production
  tab would cause the process to exceed its maximum available capacity,
  LEAP will display a diagnostic error message.
* Simulation: From the [first
  simulation year](First_Simulation_Year.md) onwards,  LEAP simulates dispatch using the
  [Process
  Dispatch Rule](Process_Dispatch_Rules.md) specified for each process.

In
earlier versions of LEAP you could only set historical production for
the base year (in a variable called Base Year Output that has now been
removed.  In the latest versions of LEAP you can specify historical
production for any years before the [first
simulation year](First_Simulation_Year.md).  Moreover, this year can vary between processes.

Tips

1. If
   you want dispatch to be simulated in ALL years (i.e. you want LEAP
   to never use Historical Production values) then set the First Simulation
   Year to a year before the base year.
2. Conversely,
   if you want LEAP to always use historical production values set the
   First Simulation Year to a year after the study end year.