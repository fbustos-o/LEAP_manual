---
Source: https://leap.sei.org/help24/Transmission/Simulation_Type.htm
---

# Simulation Type

See also: [NetworkSimulation](../18%20-%20Expressions/NetworkSimulation.md)

Used only when conducting transmission modeling as part of full energy system optimization. Transmission modeling is enabled by editing the Transmission Networks setting in the [Settings: Optimization](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Optimization) screen.

This variable is specified at the **Transmission Lines** category branch below each module, under which all of the Transmission lines (![](../assets/images/NewButtons/line.png)) are listed.  Use this variable to specify the type of simulation to be conducted:

* **None**: this option disables modeling of network flows in a particular scenario.
* **Pipeline**: this method simulates network flows as simple pipeline flows, limited only by maximum flow and efficiency.
* **DCOPF** (direct current optimized power flow): This method simulates network flows as if they were direct current flows: minimizing losses by optimizing voltage and power delivered.

Use the [NetworkSimulation](../18%20-%20Expressions/NetworkSimulation.md) function to specify these methods.  The easiest way to enter this data is to use the orange button (![](../assets/images/NewButtons/Exp%20Button.png)) attached to the variable expression.  For example, you might enter:

NetworkSimulation(Pipeline) or

NetworkSimulation(None)

As with other variables used in optimization modeling, this variable is only available for optimized scenarios.  It is not visible in Current Accounts.