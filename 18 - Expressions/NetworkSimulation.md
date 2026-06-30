---
Source: https://leap.sei.org/help24/Expressions/NetworkSimulation.htm
---

# NetworkSimulation

**S****ee also:** [Simulation Type](../09%20-%20Transmission%20Modeling/Simulation_Type.md)

## Description

This function is only used when conducting transmission modeling as part of full energy system optimization, and is only used to specify the value for the [Simulation Type](../09%20-%20Transmission%20Modeling/Simulation_Type.md) variable, which is specified at the category branch containing all of the Transmission lines (![](../assets/images/NewButtons/line.png)) in each Transformation module  The function takes a parameter that specified the type of simulation to be conducted:

* **None:** this option disables modeling of network flows.
* **Pipeline:** this method simulates network flows as simple pipeline flows, limited only by maximum flow and efficiency.
* **DCOPF** (direct current optimized power flow): This method simulates network flows as if they were direct current flows: minimizing losses by optimizing voltage and power delivered.

The easiest way to enter this function is to use the orange button (![](../assets/images/NewButtons/Exp%20Button.png)) attached to the variable expression.