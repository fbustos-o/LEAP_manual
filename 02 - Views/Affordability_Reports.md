---
Source: https://leap.sei.org/help24/Views/Affordability_Reports.htm
---

# Affordability Reports

See also: [View Bar](View_Bar.md), [Summaries View](Cost_Summary_View.md), [Decomposition Reports](Decomposition_Summary_Reports.md), [Marginal Abatement Cost Curve (MACC) Reports](Marginal_Abatement_Cost_Curve_%28MACC)_Reports.md)

![](../assets/images/NewScreens/ViewAffordability.png)

Use LEAP's optional Affordability Analysis features to examine the costs to consumers of different scenarios and how they compare to the incomes of those consumers (or the revenues of industrial consumers). The affordability of scenarios can be a good indicator of their achievability, and can also be important in helping to understand if pathways meet environmental social justice goals.

To set up an Affordability analysis, first go to the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md): Scope screen and check the box marked "Affordability". Next, go to the General: [Fuels](../16%20-%20Supporting%20Screens/Fuels.md) screen and in the "Affordability Analysis" column use check marks to indicate which fuels you wish to include in your analysis. You can include up to 10 (including electricity). Next, return to Analysis View and from the tree choose the Demand branches at which you wish to calculate affordability. For example, you may choose to examine all households together or you may choose to examine urban and rural households separately since they may have different usage patterns, different levels of income, and may be subject to different tariff structures. You can choose which Demand branches to include by right-clicking on a branch and editing its properties. Put a check mark in the "Affordability Branch" box to include the branch in your analysis.

Once you have set up the affordability analysis, you will see new variables at your chosen demand branches. At these branches, you can specify the [prices for each fuel](../21.5%20-%20Affordability/Fuel_Price.md) consumed at those branches. LEAP has a special [Tariff function](../18%20-%20Expressions/Tariff.md) that allows you to flexibly specify tiered energy pricing structures, which are common in many countries. LEAP will also include non-fuel device costs specified via the Demand Costs variable for each relevant technology. These costs must be entered as annualized values. If you want to specify actual costs of devices, you can use the AnnualizedCost function to enter a total capital cost and a device lifetime. LEAP will then spread costs out over the lifetime of the device using a standard mortgage formula, and will assume that device gets replaced at the end of their lifetime.

Note that in scenarios you may model how a sector gradually switches away from certain fuels and technologies and instead starts using new technologies and different fuels. The costs you calculate will therefore reflect the changing penetration of these fuels and technologies and what that implies for the average costs for households and businesses.

Finally, you can also specify data in the "Income" branch for the annual income of households (or the annual revenue of industrial consumers).

LEAP uses all this data to produce reports showing the total costs to consumers (fuel costs, device costs and other demand costs) as well as the average price paid for fuels, income, and annual energy-related costs as a percentage of annual income or revenue.