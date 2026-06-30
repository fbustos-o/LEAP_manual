---
Source: https://leap.sei.org/help24/TED/Environmental_Loadings_Screen.htm
---

# Environmental Loadings Factors Screen

See also: [TED,](TED_Intro.md) [TED Data Pages,](TED_Data.md) [TED Expressions](TED_Expression_Builder.md)

![](../assets/images/NewScreens/TEDExpressionBuilder.png)

The Environmental Loading Factors screen displays one effectA pollutant emission or some other direct environmental impact from the consumption or production of energy at a time for a given technology. Use the forward and back buttons at the top of the screen to move through the list of all effects defined for the technology. To add or delete effects, you will need to exit the screen and use the Add (![](../assets/images/NewButtons/Add.png)) and Delete (![](../assets/images/NewButtons/Delete.png)) buttons on the Environment tab of the TEDThe Technology and Environmental Database. data pages.

Environmental loading factors can be specified as numeric values, or they can be specified as [expressions](TED_Expression_Builder.md) that depend on the chemical composition of the fuels being consumed or produced. Click on the "..." button to use the [Expression Builder](TED_Exp_Builder.md) tool to create expression-based loading factors. Typically, a loading will be an emission factor (e.g. kg of pollutant per GJ of energy consumed), but loadings can also be specified any other unit of direct environmental impact.

Use the first row of selection boxes to choose the numerator units (e.g. pounds, kilograms or tonnes of pollutant) and denominator units (e.g. , BTUs, TJ, or TOE of energy consumed, produced or lost) in which the loading factor is to be entered. Loadings for energy supply technologies can be specified per unit of energy consumed, produced, or lost. Loadings for vehicles (for which an energy intensity per vehicle-km or per vehicle-mile are specified) can also be specified in those units.

Use the second row of selection boxes to convert the loading into some other set of units. For energy supply technologies, you can convert emission factors between loadings per unit of energy consumed (e.g. kg/GJ or kg/Tonne) and loadings per unit of energy produced (e.g. kg/GWh of electricity). Note that this feature requires that you specify the efficiency of the supply technology. Use the Quick Units buttons on the right to quickly select standard units. For vehicles, if you have specified an energy intensity per vehicle-km or per vehicle-mile, then you can convert loading factors between loadings per unit of energy consumed and loadings per unit of transportation service.

When a technology is associated with one or more pollution controls (as specified on the Environment tab of the TED data pages), the Environmental Loading Factors screen will also display the level of emission abatement from the selected controls, and the final controlled loading factor.