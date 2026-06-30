---
Source: https://leap.sei.org/help24/Transformation/Process_Dispatch_Rules.htm
---

# Dispatch Rule

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Transformation Analysis](Transformation.md)

Dispatch rules are used when a Transformation module is operating in simulation mode.  They do not apply (and are hidden) if a module is using optimization calculations.

The dispatch rule sets how a process is dispatched on and after the [First Simulation Year](First_Simulation_Year.md).  When dispatching processes to try and meet the energy and power requirements for each module, LEAP can operate in two different modes as follows:

* Historical Dispatch is used in each year before the [first simulation year](First_Simulation_Year.md).  In these years, LEAP runs each process up to the amount specified in the Historical Production variable.
* Simulation: From the [first simulation year](First_Simulation_Year.md) onwards,  LEAP simulates dispatch using the Process Dispatch Rule specified for each process.

There are 5 different rules to choose from, but only some of these may be available depending on how you set up the module.  Use the [Module Properties](Module_Properties_Wiziard.md) screen to indicate the types of data defined at each module.  The 5 dispatch rules are specified by entering one of the following constant expressions: PercentShare, ProportionalToCapacity, FullCapacity, MeritOrderDispatch and RunningCost.

Each rule is described in more detail below:

* PercentShare: This is the simplest rule in which you simply specify that a process will run to meet a certain percentage fraction of the requirements on the module (so long as there is sufficient available capacity).   For example, you may wish to specify that an electricity module produces 50% of its electricity from coal, 20% from hydro and 30% from natural gas. These shares can change over time. This rule is useful if you have results taken from the calculations of another model that you wish to include in LEAP.  For example: if you have separate electric sector projections of plant operation, you could enter those results in LEAP to check the validity of sectoral plans against the integrated planning viewpoint in LEAP.

The following dispatch rules are available only if capacity data are also specified:

* ProportionalToCapacity: With this rule, processes are dispatched to try and meet the requirements on a module.  If the available capacity exceeds the amount needed to meet requirements then each process will be dispatched in proportion to its available capacity  (Capacity * Maximum Availability).  For example, if two plants are defined and one is rated at twice the available capacity of the other then they will run to produce outputs in a ratio of 2:1.
* FullCapacity: With this rule, processes are run to produce their full available capacity regardless of the requirements on the module.  You can use this option to simulate export-driven energy industries for which the level of domestic requirements are unimportant (e.g., an export driven refinery).

The following dispatch rules are available only if capacity data and system load curve data are specified:

* MeritOrderDispatch: Use this option to simulate the dispatch of power plants to meet both the annual demand for electricity as well as the instantaneous demand for power in time slices of the year. Processes will be dispatched according to merit orders defined in the [Merit Order](Merit_Order.md) variables. Each process will be run (if necessary) up to the limit of its [maximum capacity factor](Maxiumum_Capacity_Factor.md) in each dispatch period.    
    
  Special Note: the name of this rule has recent been changed from MeritOrder to MeritOrderDispatch. This was done in order to avoid confusion between the constant denoting a particular dispatch rule, and the variable named Merit Order that contains actual values for process merit orders.

The following dispatch rule is available only if capacity data, system load curve data and costs data are specified:

* RunningCost: This option is similar to the "merit order" option except that processes will be dispatched in ascending order of their overall running costs (defined as variableData that can change over time. cost + fuelSomething combusted, or otherwise used to produce energy cost).