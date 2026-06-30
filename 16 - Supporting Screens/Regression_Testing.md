---
Source: https://leap.sei.org/help24/Supporting_Screens/Regression_Testing.htm
---

# Regression Testing

## Introduction

Regression testing can be useful if you install a new version of LEAP and want to check that it is producing exactly the same results as an earlier version, or if you make some changes to a model and want to see how those changes have affected the results.

## Using Regression Testing

Regression testing allows you to save a **definitive** version of your area (one with the correct set of results) and to test this against versions you create later (the **current** version). There are two menu options available for regression testing under the Area: **Regression Testing** menu option:

* **Save Definitive Version**: This option saves a **definitive** version of your area results.  LEAP will save all results across all calculated regions and scenarios. In addition to saving all results values, it also exports results from major reporting views including energy balances, Sankey diagrams, cost-benefit summaries, favorite charts, decomposition reports and (optionally) Marginal Abatement Costs Curves (MACCs).  All these results are saved in a folder named _RegressionTests\Definitive. In this way, regression testing serves to check both LEAP's calculations and also to check how results reports are presented in various formats.
* **Regression Test:** When you select this option, LEAP will create another saved copy of the results for your area (referred to as the **Current** version) and compare that against the previously saved **Definitive** version.  The current set of results are stored in in a folder named _RegressionTests\Current. Once the current and definitive versions have been compared, LEAP will report if the two are exactly similar and if not, what are the discrepancies between the two versions.

## The Discrepancies Screen

Once a regression test is complete, LEAP will show a summary of any discrepancies between the two versions and (if there are any discrepancies) offer to show you the Discrepancies screen in which you can examine the differences in more detail.  An example of this screen is shown here:

![](../assets/images/NewScreens/RegTest.png)

Use the filtering controls in the toolbar to filter the report by type of result, type of error, scenario, region, or year. You can also filter the report by how large the differences are between the current and definitive values. Click the grid's column titles to sort by on that column.  Click the Excel button (![](../assets/images/NewButtons/MS-Excel.png)) to export the report to Excel.

Click the summary button to see a summary of the types of discrepancies (differences in values or values missing from either the current or definitive versions) as well as the type of reports where the discrepancies occur (detailed results, energy balances, Sankey diagrams, cost-benefit summaries, decomposition reports, favorite charts, and MACCs).

## Using Regression Testing via the API

Regression testing can also be conducted using LEAP's application programming interface (API). This allows scripts to be written that can test out multiple areas in a batch.  Use the LEAP..RegressionSaveDefinitive, and LEAP.RegressionTest commands to do this.