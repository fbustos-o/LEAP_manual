---
Source: https://leap.sei.org/help24/Transformation/Endogenous_Capacity.htm
---

# Endogenous Capacity

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Exogenous Capacity](Capacties.md), [Specifying Capacity Data](Specifying_Capacty_Data_in_LEAP.md)

Note: Capacity data can only be entered for a module if it is first you specified on the [Module Properties](Module_Properties_Wiziard.md) screen.

Endogenous Capacity is capacity calculated internally by LEAP in order to maintain a minimum [planning reserve margin](Planning_Reserve_Margin.md). Endogenous capacity additions occur in addition to the exogenous level of capacity specified on the Exogenous Capacity data table.   Note that the endogenous capacity variable is not used when a LEAP module is calculated using the least-cost optimization methodology.  For more information see: [Specifying Capacity Data](Specifying_Capacty_Data_in_LEAP.md)

For endogenously added capacity, instead of specifying the total capacity additions and retirements, you create a list of the processes that are available to be added, and specify the addition size and order of addition for each process. For example, if the type of power plants that are expected to be added to an electric system consist of 500 MW coal steam power plants, balanced by 300 MW oil combustion turbines, then you would enter the following information:

![](../assets/images/Transformation/EndogenousScreen.png)

Notice that the onus is on the user to make sure that the processes specified will maintain a good balance between base load and peak load plants. In the screen shown above, 500 MW of coal steam plant will be added first (i.e. the process with addition order = 1), followed by 300 MW of oil combustion turbine plants (addition order = 2). Should further additions be required in any given year to maintain the reserve margin above the value specified on the [Planning Reserve Margin](Planning_Reserve_Margin.md) screen, then a further 500 MW of coal will be built, followed by a further 300 ME of oil and so on. Click the Add button (![](../assets/images/NewButtons/Add.png)) on the right of the screen to add a process to the list. You can select any process already defined within the module. Click the Delete button (![](../assets/images/NewButtons/Delete.png)) to remove the process from the list. Notice that deleting the process here does not delete it from the tree. Use the Up (![](../assets/images/NewButtons/Arrow-up.png)) and Down (![](../assets/images/NewButtons/Arrow-down.png)) buttons to change the order of the processes in the list (i.e. the order in which LEAP cycles through the processes during the endogenous expansion calculation). When each endogenously added process reaches its specified lifetime, it will be automatically retired (and additional processes added if necessary). When specifying, the addition size, you can use LEAP's built in expressions to specify different addition sizes as a function of years using a conditional function of the following type:

 If( Greaterthan(Year, X), AdditionSizeFirstPeriod, AdditionSizeSecondPeriod)

where X is any year, AdditionSizeFirstPeriod is the addition size on or before year X and AdditionSizeSecondPeriodand is the addition size after year X.

Note that the year in which LEAP starts adding endogenous capacity will depend upon such factors as:

* How quickly electricity requirements increase.
* The initial reserve margin (if it is much higher than the planning reserve margin then LEAP may not add extra capacity for many years), if its starting value is less than the planning reserve margin, LEAP will start adding capacity in the year after the base year.
* Whether any capacity is added exogenously.

## Specifying a Supply Curve

You can also use this screen in conjunction with the Maximum Built Capacity variable to specify a supply curve for any given addition order in which one process is built first (up to its maximum built capacity) and thereafter another process is added. Typically, currently available and/or cheaper technologies will be built first. Use the ![](../assets/images/NewButtons/Arrow-right.png) button to mark a process as a next generation technology with a later Build Order. This process will be shown on screen indented compared to the process above it, and during calculations will only be added once the Maximum Built Capacity of the earlier generation process has been reached. Use the ![](../assets/images/NewButtons/Arrow-left.png) button to reverse this.