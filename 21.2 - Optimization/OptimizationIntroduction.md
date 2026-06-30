---
Source: https://leap.sei.org/help24/Optimization/OptimizationIntroduction.htm
---

# Introduction to Optimization

See also: [Setting Up Optimization in LEAP](Setting_Up_Optimization_in_LEAP.md)

## Introduction

LEAP supports a wide variety of methodologies for integrated energy system analysis.  These include simulation-based approaches such as econometric or end-use oriented simulation and optimization methods.  You can mix and match methods and even use different methods in different scenarios - allowing you to compare the results from using these different methods.

Optimization calculations in LEAP work through integration with **N**EMO.  NEMO is an open source framework built in the [Julia](https://docs.julialang.org/en/v1/) programming language: a fast, flexible language that excels at scientific and numerical computing.  NEMO must be installed separately from LEAP but is freely available for [download from the LEAP web site](https://leap.sei.org/download). No additional license is required and there is no additional cost involved in using NEMO with LEAP. Once installed, NEMO is seamlessly connected to LEAP.

LEAP works with NEMO to support both **partial cost optimization** modeling for just a single Transformation module (e.g. electricity generation)  or it can be used to conduct **full energy system optimization (ESO)** modeling.  ESO modeling supports modeling simultaneous least-cost optimization calculations across all Transformation modules and can also optionally incorporate optimization of selected demand end uses (any end uses specified with a useful energy demand).  ESO modeling can also include optimized modeling of transmission systems (e.g. electricity networks and pipelines).

Optimization frameworks calculate the least-cost capacity expansion and dispatch of all processes in a system, where optimal is defined as the energy system configuration with the lowest total net present value of the social costs of the system over the entire period of calculation (from the base year through to the end year), subject to various constraints such as meeting energy demands, or limiting emissions.

In calculating an optimal system LEAP takes into account all of the following relevant costs and benefits incurred in the system including:

* The capital costs for building new processes.
* The salvage values (or decommissioning costs) for decommissioning processes
* The fixed and variable operating and maintenance costs
* The fuel costs
* The environmental externality values (i.e. pollution damage or abatement costs).

Optimization modeling in LEAP can incorporate many different constraints including minimum and maximum penetrations for individual technologies and groups of technologies (e.g. a renewable portfolio standard), maximum reserves of domestic primary resources, minimum and maximum levels of imports and exports, and maximum levels of emissions of any pollutant (e.g. a cap on CO2 emissions).  Optimization  in LEAP can also incorporate externality values such as carbon prices or damage costs for any other pollutant.

The optimality of a given pathway may be very sensitive to input assumptions such as future capital costs, future efficiency assumptions, future fuel costs or future GHG mitigation targets. A system that is optimal for a country under one set of assumptions (e.g. low growth in fuel prices) may be far from optimal under another set of assumptions (e.g. high growth in oil prices).  Generally, the goal in energy planning is not to identify a single optimal solution, but rather to identify robust energy policies that work well under a range of plausible input assumptions.   You can easily use LEAP’s scenario capabilities to conduct sensitivity analysis that explores different optimal solutions under different sets of input assumptions.

Optimization modeling is currently only available for energy sector modeling. Optimization for non-energy sectors is not yet supported. However, you may combine optimized modeling of energy sectors (Demand and Transformation) with simulation-based modeling of non-energy sectors.

## Controlling Optimization in LEAP

Users of LEAP need never interact directly with NEMO or any of its data or results files. LEAP automatically writes the data files required by NEMO. Similarly, optimization results calculated by NEMO are automatically read and displayed in LEAP using its Results, Energy Balance and Cost-Benefit reports.  LEAP also automatically handles all unit conversions necessary for reading and writing the data files required by NEMO.

Optimization modeling calculates both capacity expansion (e.g. how many megawatts of power plants are built) and process dispatch (e.g. how many megawatt-hours of each power plant will be dispatched in each time slice of each year).

You can easily control which scenarios use optimization.

* **Partial Optimization:** For partial optimization of just a single Transformation model, navigate to the [Optimize](../08%20-%20Transformation/Optimize.md) variable located at the module you want to optimize and change its value from No to Yes. See [this page](../18%20-%20Expressions/Yes.md) for advanced optimization configuration options. Once you have done this, you will find additional variables become visible for the module's processes. These variables allow you to specify constraints  for the optimization calculations.  Notice that optimization is only valid in scenarios.  Thus, the Optimize variable (and the process constraint variables) will not be visible when editing Current Accounts.  When editing processes in an optimized scenario you will also notice that some of the variables that are visible in simulation scenarios are no longer visible because they are not required for optimization.  For example, the [Endogenous Capacity](../08%20-%20Transformation/Endogenous_Capacity.md) variable is hidden because LEAP and NEMO  (rather than you, the user) will decide when capacity should be added.  Similarly, the [Dispatch Rule](../08%20-%20Transformation/Process_Dispatch_Rules.md), [Process Share](../08%20-%20Transformation/Process_Shares.md) and [Merit Order](../08%20-%20Transformation/Merit_Order.md) variables are also hidden because LEAP and NEMO will decide how much of each process to utilize. Note that only one module can be enabled for partial optimization.  If you set the Optimize variable to yes in more than one module then LEAP will report an error during calculations.

* **Full Energy system Optimization:** To enable full energy system, navigate to the Energy System Optimization variable located at top level (area) branch and change its value from No to Yes. See [this page](../18%20-%20Expressions/Yes.md) for advanced optimization configuration options. Once this variable is set to yes, you will no longer see the individual Optimize variable at each Transformation module.  Once full energy system optimization is switched on you will see the same basic set of constraint variable described above but these will now be available at all processes across all Transformation modules.  In addition, you will see variables listed under the primary and secondary resource branches allowing you to enter constraints describing available resources, minimum and maximum levels of production, and minimum and maximum levels or fuel exports and imports.  You will also be able to enable optimization of any demand-side end-uses that are specified with useful energy demands.  For these branches (![](../assets/images/NewButtons/Tree/FolderGreen.png)), you will see an additional variable named [Optimize Devices](../05%20-%20Demand/Optimize_Devices.md).  If you set that variable to Yes, additional variables will appear allowing you to specify the needed input data and set constraints on the optimization of the various technologies (![](../assets/images/NewButtons/Tree/Technology%20Green.png)) below the end use.

NB: if you do not see the [Optimize](../08%20-%20Transformation/Optimize.md) or [Energy System Optimization](../08%20-%20Transformation/Energy_System_Optimization.md) variables, make sure that NEMO is properly installed alongside LEAP.  Optimization requires the presence of NEMO.

## Implicit Reference Energy System

In most least-cost energy system models, you are required to explicitly specify a detailed Reference Energy System.  A Reference Energy System (RES) is a network representation of all of the technical activities required to supply various forms of energy to end-use activities (Beller, M., 1976).  In LEAP,  the  RES is implicitly and automatically specified based on the ordering and the properties of the modules.  LEAP will automatically create the connections between resources, module's, processes end-use demands, ensuring (for example) that electricity generated in a lower down Electric Generation module is properly routed through a higher-up transmission & distribution module, and preventing the optimization calculations from unrealistically avoiding the losses inherent in transmission and distribution.  By default, LEAP assumes that the [feedstock](../08%20-%20Transformation/Feedstock_Fuel_Shares.md) and [auxiliary](../08%20-%20Transformation/Auxiliary_Fuel_Use.md) input fuels that are input to each process are sourced from the production of module's lower down in the list of Transformation modules.  However, for finer-grained control, you can override this default assumption and explicitly specify the source module for each input fuel.  Use the [Fuel Source](../08%20-%20Transformation/Fuel_Source.md) variable combined with the [SourceModule](../18%20-%20Expressions/Source_Module.md) function to specify the source for any particular input.

## Perfect Foresight vs. Limited Foresight Optimization

LEAP and NEMO support both perfect foresight and limited foresight optimization.  Limited foresight optimization is a technique for simulating planning under incomplete knowledge of future events, while perfect foresight optimization assumes complete knowledge. 

With perfect foresight optimization, all years are optimized at the same time. With limited foresight optimization, years are divided into groups, each of which is separately optimized. Results from each group provide the starting conditions for the next group.  With both limited foresight and perfect foresight optimization, you can elect to calculate selected years only, using the **Results Every** option on the [Settings:Years](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Years) screen. LEAP allows you to easily create and compare multiple scenarios, each of which can simulate different degrees of foresight. Limited foresight optimization requires use of NEMO v2.2 or later. To enable limited foresight optimization, specify additional parameters to the [Yes function](../18%20-%20Expressions/Yes.md) containing the list of years defining the yearly groups used limited foresight optimization.  Perfect foresight optimization is enabled by default when this list of years is omitted.

## Controlling the Solver Used for Optimization Calculations

For additional control over which solver is used with NEMO, including controlling what solver will be used, you can enter additional parameters to the [Yes function](../18%20-%20Expressions/Yes.md).

## More information

* [Steps for Setting Up Optimization in LEAP](Setting_Up_Optimization_in_LEAP.md)
* [NEMO Documentation](https://sei-international.github.io/NemoMod.jl)