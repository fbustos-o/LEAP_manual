---
Source: https://leap.sei.org/help24/Concepts/Transformation_Cost_Calculations.htm
---

# Cost Calculations

See also: [Demand Costs](../05%20-%20Demand/Demand_Cost_Analysis.md), [Transformation Costs](../08%20-%20Transformation/Capital_Costs.md), [Cost-Benefit Analysis](Social_Cost-Benefit_Analysis.md)

![](../assets/images/Concepts/Costs.gif)

LEAP performs cost-benefit calculations from a societal perspective by counting up all of the costs in the energy system and then comparing the costs of any two scenarios.  LEAP can include all of the following cost elements:

* [Demand costs](../05%20-%20Demand/Demand_Cost_Analysis.md) (expressed as total costs, costs per activity, or costs of saving energy relative to some scenario).
* Transformation [capital costs](../08%20-%20Transformation/Capital_Costs.md)
* Transformation [module costs](../08%20-%20Transformation/Module_Costs.md)
* Transformation fixed and variable [operating and maintenance costs](../08%20-%20Transformation/Operating_and_Maintenance_Costs.md).
* Costs of indigenous resources
* Costs of imported fuels
* Benefits of exported fuels
* [Externality costs](../04%20-%20Effects/Externality_Costs.md) from emissions of pollutants
* Costs of unmet requirements (i.e. unserved demands).

To set-up costing in LEAP it is first necessary to draw a consistent boundary around your system, so that LEAP will not double count costs and benefits.  For example, if you count the costs of fuels used to generate electricity you should not also count the cost of the electricity in an overall cost-benefit calculation.

If you have not already done so, switch on costing by going to the Scope tab of the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen and enabling costs.  Now go to the Costing tab and select the boundary you will draw around the system for the purposes of costing.

* By default, LEAP draws a boundary around the complete energy system, meaning that fuel costs are accounted for only when they are imported or exported or when indigenously produced  fuels are extracted as primary resources.
* You may wish to specify a smaller boundary.  For example, you may have data on the costs of refined and imported oil products being used in your country, but not have any data about the capital and operating costs of your refinery system.  In this case you would select a boundary that excludes a Transformation refining module (for example, you might select the boundary as the inputs to an electricity generation module).  LEAP will then ignore any capital and operating and maintenance costs in any modules below the electricity generation module.  In this case instead of accounting for the costs of crude oil, LEAP will account for the costs of oil products, using the values specified in a variable marked Delivered Costs.  This variable like all other fuel cost variables is accessed under the Resources branches in the tree.

Note: all of the cost calculations in LEAP are performed in real (constant) currency units.  However, results can be displayed in discounted currency units.  By default, LEAP use the default discount rate specified on the Defaults tab of the General: Settings screen.  Costs are discounted back to the base year of any study.

In [Cost-Benefit Reports](../02%20-%20Views/Cost_Summary_Report.md) view you can display the Net Present Value (NPV) of each scenario relative to another selected scenario.  The NPV is the sum of all discounted costs and benefits in one scenario minus another (summing across all years of the study)