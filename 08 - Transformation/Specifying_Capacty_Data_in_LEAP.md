---
Source: https://leap.sei.org/help24/Transformation/Specifying_Capacty_Data_in_LEAP.htm
---

# Specifying Capacity Data

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Exogenous Capacity](Capacties.md) [Endogenous Capacity](Endogenous_Capacity.md), [Optimized Capacity](Optimized_Capacty.md)

![](../assets/images/Transformation/DataNeeds.png)

Capacity data can be specified in different ways in LEAP. In choosing how to enter data, it may be helpful consider these four possible approaches:

* Ignore Capacity Limits: In this, the simplest approach you can simply ignore any possible capacity constraints in a Transformation module.  This approach can be useful in cases where you have no data on the capacities of processes or for modules where capacity limits are not an important issue.  For example, if you are modeling an informal sector such as charcoal making, you probably won't need to consider actual production capacity of charcoal kilns, since these are typically managed on a very small scale or informal basis.  If you wish to use this the simple approach you will only be able to specify the share of each process using the [Process Share](Process_Shares.md) variable.  To configure this approach, go to the [Module Properties](Module_Properties_Wiziard.md) screen and make sure the Capacities check box is left unchecked for your module.
* You Control What Capacity to Add and When it will be Added:  In this second approach, you can use the [Exogenous Capacity](Capacties.md) variable to specify the exact amounts and dates when future capacity additions will be made.  To configure this approach, go to the [Module Properties](Module_Properties_Wiziard.md) screen and make sure the Capacities checkbox is checked (switched on) for your module.
* You Control What Capacity to Add, But LEAP Controls When it will be Added:  In this third approach (which builds on the above approach), you still use the [Exogenous capacity](Capacties.md) variable to specify previously existing capacity as well as planned or committed capacity additions and retirements; but in addition you can also the [Endogenous Capacity](Endogenous_Capacity.md) variable to cause additional capacity to be added automatically.  Using this variable, you still control exactly which types of capacity will be added, but LEAP will decide the dates WHEN those plants will be added.  It does this by monitoring the module's reserve margin and adds plants as needed in order to keep the reserve margin above the [Planning Reserve Margin](Planning_Reserve_Margin.md) you specify at the module level.

Notice that the above three approaches are NOT guaranteed to result in a least-cost energy system configuration. However, a third approach is also available:

* LEAP Controls What Capacity to Add and When it Will be Added.  In this fourth approach, LEAP uses a [least-cost optimization methodology](../21.2%20-%20Optimization/OptimizationIntroduction.md) to decided what types of capacity should be added and when it will be added.  Optimization also controls the dispatch of processes.  Optimization can be switched on for a particular module and a particular scenario using the [Optimize](Optimize.md) variable specified at the module level.  Thus, you can compare the results of different scenarios, some using optimization and some using the previously-mentioned simulation-based approaches.

Notice how, with these four approaches, you are gradually handing over more and more decision-making control to the model.  Bear in mind also that using an optimization approach requires more data than the previous two approaches.  In particular it requires that data describing the [capital](Capital_Costs.md), [O&M](Operating_and_Maintenance_Costs.md) and [fuels costs](Fuel_Costs.md) for each process are fully defined.  By contrast, the other three approaches can be used without any cost data being entered.