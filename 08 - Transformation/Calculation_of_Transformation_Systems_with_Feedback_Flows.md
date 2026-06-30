---
Source: https://leap.sei.org/help24/Transformation/Calculation_of_Transformation_Systems_with_Feedback_Flows.htm
---

# Calculation of Systems with Feedback Flows

See also: [Transformation Calculations](Transformation_Calculations.md), [Auxiliary Fuel Use](Auxiliary_Fuel_Use.md)

To accommodate more complex energy supply systems, the Transformation calculations allow for energy systems with energy flow feed backs. For example, in the diagram shown below, an oil refinery might produce diesel for use in power generation, while the oil refinery itself might consume some of the generated electricity.

These systems are solved by repeating (iterating) the basic Transformation calculation, but with adjustments made to total demands after each iteration to reflect any unmet requirements for upstream energy flows.

![](../assets/images/Transformation/looping.gif)

1. In the figure shown above, a final demand for 100 units of electricity is met by a power plant using diesel and operating at 33% efficiency. This, in turn, requires 300 units of diesel, which are produced by a simplified (one product) refinery operating at 94% efficiency. Thus, the overall demand for crude oil is 320 units. To produce the diesel, the oil refinery itself uses 5 units of electricity. In the first calculation iteration, these 5 units of electricity demand remain unmet by the system .
2. In the second iteration, the 5 units of unmet requirements are added to the final energy demand that drives the calculation. This causes the power plant to generate 105 units of electricity using 315 units of oil. This, in turn, requires that the refinery uses 320 units of crude and 5.25 units of electricity.
3. The third iteration begins with the generation of 105.25 units of electricity, and iterations continue until successive changes in the electricity requirements become small. At this point, the system has converged to a solution.

Important:

* LEAP will only iterate calculations for fuels and which have had their resource properties set to allow for iterative calculations. To make this setting for a fuel go to one of the Resource branches and set the properties for the fuel in question to Iterate Calculations: Use upstream modules to meet any remaining requirements.
* Note that it is possible to create systems that will not converge. If convergence is not reach within 20 iterations, or if the calculations tend to diverge, then LEAP will report an error and halt the whole calculation.