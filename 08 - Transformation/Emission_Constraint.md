---
Source: https://leap.sei.org/help24/Transformation/Emission_Constraint.htm
---

# Annual Emission Constraints

Annual Emission constraints
are specified under a top-level branch of the LEAP Tree.  They are
only used (and are only relevant) when running scenarios that include
least cost optimization of a Transformation module.

Go to the Optimization screen of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Optimization)
screen to enable display and calculation of emission constraints.

Emissions constraints can be used to specify a maximum annual level
of emissions for any specified pollutant.  LEAP's optimization calculation
will then be used to try and identify a least cost configuration of a
Transformation module that keep total emissions of pollutants (across
the whole energy system) below the specified annual emissions constraint.

In LEAP, emissions of pollutants may arise from various parts of the
system, including from Demand sectors, Transformation modules and Non
energy sectors.  The values entered for the emission constraint variable
are the maximum desired value for emissions across all parts of the system.
 However, LEAP's optimization calculations normally only operate
on a single Transformation module (typically the electric generation module).

Use the expression [Unlimited](../18%20-%20Expressions/Unlimited.md)
if you do not wish to specify a constraint.

Note: Emissions
constraints are not relevant (and will be ignored) for any scenarios calculated
without
least cost optimization calculations.