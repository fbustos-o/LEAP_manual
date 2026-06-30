---
Source: https://leap.sei.org/help24/Transformation/Renewable_Target.htm
---

# Renewable Target

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Renewable Qualified](Renewable_Qualified.md)

Minimum percentage of fuel requirements that should come from the processes marked as being renewable (using the Renewable Qualified variable). Used to specify a generation target in a Renewable Portfolio Standard (RPS).  Only applicable in optimization-based scenarios.

Note you should mark each process as being [Renewable Qualified](Renewable_Qualified.md) at the process level.  Take care: it is possible to mark any process as being renewable regardless of what feedstock fuel it actually uses.  Normally you would want to mark wind, solar, hydro, biomass, etc. as being renewable qualified.  However, in some situations hydro, and biomass projects may not qualify for an RPS.

Note: this variable was previously located at load shape branches. It is now located at Transformation modules.