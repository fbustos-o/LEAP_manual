---
Source: https://leap.sei.org/help24/Transformation/Module_Properties_Wiziard.htm
---

# Module Properties

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Transformation Analysis](Transformation.md), [Specifying Capacity Data](Specifying_Capacty_Data_in_LEAP.md), [Process Properties](Module_Properties_Wiziard.md)

![](../assets/images/NewScreens/TransformationModuleProperties.png)

Use the Module Properties screen to edit the name and set the properties of each Transformation module. These settings will determine which data are shown in the [Analysis View](../02%20-%20Views/Data_View.md), and how the module will be treated during LEAP's calculations.  Notice that some settings will only be visible when other settings have been chosen. In particular, when you choose Simple Non-Dispatched Module, most other settings will be hidden.

Once you have create a module it is currently not possible to change its type (from simple non-dispatched to standard or vice versa).  If you need to change the type you will need to delete the module and re-enter all data.

## Simple, Non-Dispatched Module

Check this box if you wish to create a Simple Non-Dispatched Module.  This is used in cases where you have one or more independently dispatched processes, each of which has its own output fuel.  This type of module is particularly useful when you want to represent transport losses in a number of different fuels.  For this type of module, the separate output fuels branch category  is not used. Instead, you pick the output fuel for each process on the efficiency or loss tab.  For more information, see the [schematic diagrams of Transformation modules](Schematic_of_Standard_Module.md).

Please note that once you have created a simple module, it is not possible to change it to become a standard (detailed) module or versa.  If you create a module of the wrong type, you will need to delete it from the tree and then recreate it.

## Types of  Data to Include

Use these settings specify which types of data are to be entered for the module.

* Costs: If you do not intend to include cost data, then you can uncheck this option to reduce the number of data tabs shown on the process data entry screens.
* Capacities: Processes without capacity data operate without capacity restrictions.  These processes require less data and are generally easier to set-up and debug, but may not fully reflect real-world situations. Note also, that if you leave this setting unchecked then all of the capacity-related  data such as the [Exogenous Capacity](Capacties.md) and [Endogenous Capacity](Endogenous_Capacity.md) variables, System Load Data and most [Dispatch Rules](Process_Dispatch_Rules.md) will be unavailable.
* **Planning Reserve Margin calculated endogenously:** Normally, if you specify capacity data you will also need to specify a [planning reserve margin](Planning_Reserve_Margin.md) for the module. In simulation scenarios only, you can opt to have LEAP estimate the required planning reserve margin.
* Coproduct: If you wish to simulate one or more processes that cogenerate heat and electricity, then check this setting and select the cogenerated fuel. Typically, you will specify electricity as your main Output fuel, and heat as the coproduct fuel or vice-versa. This approach is generally recommended instead of specifying two separate output fuels, since it allows each process to produce different fractions of heat and electricity (by specifying separate efficiencies for the main output fuel(s) and the cogenerated fuel). Note also, that it is possible to specify that only a subset of processes produce a coproduct. For example, some thermal plants may produced heat, while hydro and wind plants will not. This is done by entering different values for the coproduct share for different processes.
* Output Shares: Use this box to specify whether you want to explicitly enter data on Output Shares (the share of total energy output from provided by each fuel). If this setting is not checked, then output shares will be calculated in proportion to the requirements on the module. This option has no effect if a module has only one output fuel.
* Try to Meet auxiliary fuel use from module's outputs: Feedback flows are often caused by situations in which a fuel is consumed in one Transformation module but produced only by a higher up module, leading to LEAP needing to attempt a series of iterative calculation to fully resolve energy flows in an energy system.  For situations where an auxiliary fuel used in a module is also a product of the module, you can treat that auxiliary fuel as "own use" consumption and avoid the need for more complex iterative calculations.   Use this option to tell LEAP that the outputs of the module should be used to meet the auxiliary fuel use requirements where possible.  In this circumstance the outputs from the module will be the net amount (after deducting auxiliary fuel use requirements).  If the option is switched off, then the outputs will be the gross outputs and auxiliary fuel use needs will need to be resolved in lower down modules (or through imports of the fuel).  If auxiliary fuels are not a product of the module then this switch will have no affect.  See [Auxiliary Fuel Use](Auxiliary_Fuel_Use.md) help page for more information.

## Enter Efficiency Data As

Use this box to specify how efficiency data is to be entered: as a percentage thermal efficiency (i.e. energy output per unit of energy input), as a heat rate (i.e. energy input per unit of energy output), or as a percentage loss. Note that when using heat rates, all processes must be specified with the same units (e.g. TOE/MWh).

## Transmission Networks

When your model includes [transmission modeling](../09%20-%20Transmission%20Modeling/Setting_Up_Transmission_Modeling.md), you will see additional options in the Module properties screen used to  configure transmission network modeling.  Use the check boxes to specify if **transmission lines connect at the module**, and whether to **Distribute process capacity to nodes using the same shares used to distribute module energy requirements.**   This later option simplifies data entry by not requiring separate allocations of nodal capacity and nodal energy requirements.  
  
You will also see additional options that can be used to set up how you want to enter data for **transmission** **costs** (total, per unit distance, or per unit of transmission capacity) and **transmission losses** (as efficiencies, as losses, or as losses per unit of distance).