---
Source: https://leap.sei.org/help24/Results_Categories/Costs.htm
---

# Social Costs

See also: [Results View](../02%20-%20Views/Results_Screen.md), [Transformation Module Costs](Module_Cost_Balance.md), [Investment Costs](Investment_Costs.md)    
Result Type: Costs

This result type shows overall social costs for your scenarios. These costs represent the overall costs to society of a scenario as opposed to the particular costs of production seen by producers or consumers.

You can view social cost results by each different type of cost element including:

* Demand Costs including costs specified as [device costs and as costs of saved energy](../05%20-%20Demand/Demand_Cost_Analysis.md). Note that demand costs typically exclude the price of any fuels used in demand devices.  Fuel costs are captured separately based on the production, import and export costs specified under your resource branches.
* Transformation Costs including, [capital costs](../08%20-%20Transformation/Capital_Costs.md), [module costs](../08%20-%20Transformation/Module_Costs.md), and fixed and variable [operating & maintenance costs](../08%20-%20Transformation/Operating_and_Maintenance_Costs.md), but excluding the [fuel costs](../08%20-%20Transformation/Fuel_Costs.md) specified for your Transformation Feedstock fuel branches.  Note that these feedstock fuel costs are used when calculating the costs of production and can potentially be different from the costs used in the social costs calculation.
* Fuel Costs: In order to avoid the potential for double-counting costs, LEAP draws a user-specified boundary around the energy system and only counts fuel costs at the point where those fuels cross that boundary. Typically you will draw the boundary around the entire system and thus calculate the fuel component of the social costs by including the [indigenous production and import costs and export benefits](../10%20-%20Resources/Resource_Costs.md) of exported fuels as specified under your Resource branches.  You can specify the boundary used for calculating social costs on the [costing tab](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Costing_Methodology) of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen.
* Environmental externalities: if specified for any particular pollutants.  To specify externalities, make sure you switch on Environmental Externality Costs in the [Costing](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Costing_Methodology) tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen. [Externality costs](../04%20-%20Effects/Externality_Costs.md) can be specified under the top level Effects branch after adding particular effects.

* Costs of Unmet Requirements: This category calculates the economic damage associated with unmet energy requirements, such as (for example) the economic cost of power blackouts.  You can specify these costs using the [Cost of Unmet Requirements](../10%20-%20Resources/Resource_Costs.md) variable found under the Resource branches.

Note: Cost results are only available if you have specified cost data and if you have switched on the costing  analysis in the Scope and Scale tab of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md): screen.