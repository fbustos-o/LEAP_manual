---
Source: https://leap.sei.org/help24/Transmission/Nodal_Distribution.htm
---

# Nodal Distribution

See also:

Used only when conducting transmission modeling as part of full energy system optimization. Transmission modeling is enabled by editing the Transmission Networks setting in the [Settings: Optimization](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Optimization) screen.

This variable is specified for each Transmission node (![](../assets/images/NewButtons/node.png)).  Use it to specify the share of energy requirements by node (%).  Shares must sum to 100% across all nodes in each region in each module. By default, process capacity is allocated to nodes using the same nodal shares used to allocate energy requirements.  If you want to override this default behavior you can do so by changing the default settings of the [module properties](../08%20-%20Transformation/Module_Properties_Wiziard.md) screen.  If you do this you will also need to specify the nodal distribution of capacity for each process in the module. Again, shares must sum to 100% across all nodes for each process in each region in each module.

As with other variables used in optimization modeling, this variable is only available for optimized scenarios.  It is not visible in Current Accounts.