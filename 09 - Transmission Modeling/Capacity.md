---
Source: https://leap.sei.org/help24/Transmission/Capacity.htm
---

# Transmission Capacity

See also:

Used only when conducting transmission modeling as part of full energy system optimization. Transmission modeling is enabled by editing the Transmission Networks setting in the [Settings: Optimization](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Optimization) screen.

This variable is specified for each Transmission line (![](../assets/images/NewButtons/line.png)).  Use it to specify the maximum power flow supported by a transmission line or pipeline. The variable uses power units (e.g. MW, GJ/Day, BTU/Hour, etc.)

As with other variables used in optimization modeling, this variable is only available for optimized scenarios.  It is not visible in Current Accounts.

If you want to specify pre-existing (i.e. exogenous) transmission capacity, you can create a transmission line with a value for capacity and also specify a [construction year](Construction_Year.md) prior to the first scenario year.  That way, your scenario will not incur any capital costs for building the line but the optimization calculations will still decide whether or not it makes sense to use the line.