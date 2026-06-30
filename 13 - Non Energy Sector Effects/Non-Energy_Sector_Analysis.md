---
Source: https://leap.sei.org/help24/Non-Energy/Non-Energy_Sector_Analysis.htm
---

# Non Energy Sector Effect Loading

**S**ee also: [Analysis View](../02%20-%20Views/Data_View.md), [Non Energy Sector Effect Costs](Non_Energy_Sector_Effect_Cost.md)

![](../assets/images/NewScreens/NonEnergyEffectProperties.png)

LEAP also optionally lets you create inventories and scenarios for Non-energy related effects. Typically you can use this feature for including inventories and scenarios of non-energy sector greenhouse gas (GHG) emissions, as a complement to the analysis of energy sector greenhouse gas emissions and mitigation measures conducted in the other parts of LEAP.

To set-up an analysis of non-energy sector effect, first select the [Analysis View,](../02%20-%20Views/Data_View.md) then go to the Scope tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen and make sure the Non Energy Sector Effect Loadings box is checked. An additional top-level category branch (![](../assets/images/NewButtons/Tree/folder.png)) will appear marked Non Energy. Non energy sector effects are analyzed by creating a hierarchical structure of effects under this top-level branch in much the same way that you create a hierarchical tree structure to analyze energy demands. The structure will consist of category branches (![](../assets/images/NewButtons/Tree/folder.png)) used only for organizational purposes, and effect branches (![](../assets/images/NewButtons/Main%20Toolbar/effects.png)) at which you specify annual total emissions loadings. Use the standard tree editing controls to manipulate the tree structure including: Add (![](../assets/images/NewButtons/Add.png)), Delete (![](../assets/images/NewButtons/Delete.png)), and Properties (![](../assets/images/NewButtons/Properties.png)).

When you click, the Add or Properties buttons, you will be shown a small dialog box in which you specify the name and branch type. You can analyze any effect listed in the [effects database](../16%20-%20Supporting%20Screens/Effects_Screen.md). Effects are specified in the relevant units for each effect. Typically most effects are measured in mass units.

Unlike an energy demand analysis in which total effects are calculated as the product of energy consumption and an emission factor, in the Non Energy Sector you simply specify total annual non [effect loadings](Non-Energy_Sector_Analysis.md) (and optionally [effect costs](Non_Energy_Sector_Effect_Cost.md)). Of course you can use LEAP's expressions to calculate the total loading as a function of one or more independent variables. As in your energy analysis, you can analyze any number of different scenarios.