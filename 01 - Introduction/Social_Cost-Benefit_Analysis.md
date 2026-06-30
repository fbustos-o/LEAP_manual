---
Source: https://leap.sei.org/help24/Concepts/Social_Cost-Benefit_Analysis.htm
---

# Cost-Benefit Analysis

See also: [Demand Analysis](../05%20-%20Demand/Demand.md) , [Transformation Analysis](../08%20-%20Transformation/Transformation.md) , [Cost Calculations](Transformation_Cost_Calculations.md)

You can use LEAP to perform integrated social cost-benefit analysis on the scenarios you create. The [Cost-Benefit View](../02%20-%20Views/Cost_Summary_Report.md) is the main tool for cost-benefit comparisons of scenarios.

LEAP's cost-benefit analysis calculates the costs of each part of the energy system: the capital and operating maintenance costs of purchasing and using the technologies in the Demand and Transformation systems; the costs of extracting primary resources and importing fuels and the benefits from exporting fuels. In addition you can also optionally broaden the scope of your cost-benefit calculations to examine environmental externalities, by assigning costs to the emission of pollutants and any other direct social and environmental impacts of the energy system.

When comparing scenarios, it is important that only those scenarios with similar economic assumptions be compared. For example, it would be inappropriate to compare two scenarios with different population or GNP growth rates, since those factors are not part of the energy policies being considered.

Cost-benefit analysis is based on the social costs of resources, not the final prices of energy to the consumer. Cost-benefit analysis centers on the costs (sometimes called the "opportunity costs") to society of a given set of actions. It does not take the perspective of a particular consumer or producer. Social costs and prices need not be the same. For example, electricity prices may differ from the costs of producing electricity, due to subsidies, transfer payments and market distortions.

Cost-benefit analysis in LEAP is not intended to provide an analysis of financial viability. Instead, it helps identify a range of socially-acceptable policy scenarios. Detailed financial analysis can then be carried out to identify which scenarios are also financially acceptable.

To provide flexibility in how a cost-benefit analysis is conducted, LEAP allows you to specify a costing boundary: the Transformation moduleA Transformation branch representing an energy industry or sector, such as electricity generation, oil refining, district heating, charcoal production, or electricity transmission and distribution after which costs associated with energy conversion and extraction are no longer counted. Specifying a limited boundary that does not encompass all modules, can be very useful for modeling systems in which you only have data on the costs of fuels as they are consumed, and you do not have data on the costs of upstream technologies such as oil refining and coal mining. For example, you might specify the boundary as electricity production. This means: a) that LEAP will not consider capital and O&M costs for upstream activities (modules) such as oil refining or coal production; and b) that costs will be applied to the feedstockAn input fuel consumed by a Transformation conversion process. fuels delivered to electricity plants (e.g.,. diesel) rather than to the resources (e.g. crude oil) from which they are produced. For more information on setting-up costing boundaries, see the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen.