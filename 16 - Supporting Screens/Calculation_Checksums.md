---
Source: https://leap.sei.org/help24/Supporting_Screens/Calculation_Checksums.htm
---

# Calculation Check sums

Menu Option: General: Calculation Checksums  
See also: [Diagnostics](../02%20-%20Views/Diagnostics.md)

Check sums can be an important tool for debugging your analyses. You can optionally define check sums for two categories of results: the total final demand and/or the total primary requirements of fuels in a particular year and scenarioA self-consistent story line of how a future energy system might evolve over time in a particular socio-economic setting and under a particular set of policy conditions. . During LEAP calculations, these check sums will be compared to the calculated demand or primary requirements, and where the discrepancy is greater than the allowed percentage, a diagnostic message will be shown. Diagnostic messages are displayed as an additional tab on the [Results View](../02%20-%20Views/Results_Screen.md) (alongside the Chart and Table tabs). When no diagnostic messages exist, the Diagnostics tab is not visible. For more information, see [Diagnostics](../02%20-%20Views/Diagnostics.md).

There are two basic methods for entering check sums. Either you can add them manually on this screen, or you automatically save a complete set of check sums from within the [Results](../02%20-%20Views/Results_Screen.md) View (select menu option Area: Create Check sums). We suggest that once you have a fully completed scenario, you create a set of check sums for it using this option. In this way, any subsequent accidental changes to the scenario can be immediately identified, whenever results are recalculated.

When entering check sums manually, use the scenario selection box to first pick a scenario, then use the Add (![](../assets/images/NewButtons/Add.png)) button to add a new checksum the Delete button (![](../assets/images/NewButtons/Delete.png)) to delete a checksum. When adding a checksum you will be asked to select the fuelSomething combusted, or otherwise used to produce energy and year for which you wish to enter the data. If you wish to specify the checksum for only one of the two categories, simply leave the other one blank.