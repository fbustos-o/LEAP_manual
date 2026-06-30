---
Source: https://leap.sei.org/help24/Transformation/Transformation_Calculations.htm
---

# Transformation Calculations

See
also: [Transformation
Analysis](Transformation.md)

Transformation calculations are demand-driven. That is, each moduleA Transformation branch representing an energy industry or sector, such as electricity generation, oil refining, district heating, charcoal production, or electricity transmission and distribution is operated to meet the demands
that arise from domestic requirements and export demands (net of any minimum
specified level of imports). For the first calculated module (the one
closest to demands), domestic requirements are set equal to final demands
(see [Demand Calculations](../05%20-%20Demand/Demand_Calculations.md)).
After each module is calculated, domestic requirements are decremented
by the outputs produced from the module, but incremented by the input
fuels required by the module. Ultimately the calculation yields the requirements
for primary resources (fossil and renewable), which can be compared to
the amounts specified in your Resource branches.

Note that the ordering of modules will effect calculation results. Before
calculating make sure you modules are in the correct order in the tree.
(e.g., an electric transmission & distribution module should lie above
an electric generation module).