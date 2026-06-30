---
Source: https://leap.sei.org/help24/Views/Diagnostics.htm
---

# Diagnostics

See also: [Detailed Results View](Results_Screen.md), [Calculation Checksums](../16%20-%20Supporting%20Screens/Calculation_Checksums.md)

During its calculations, LEAP performs a number of different checks on your data set. The outcome of these checks are reported as diagnostics messages, which are displayed on the Diagnostics tab of the [Detailed Results View](Results_Screen.md). The Diagnostics messages are displayed in table form showing the branch, scenario and year for which the message was generated. When no diagnostic messages are generated, the Diagnostics tab is not visible. Some diagnostics measures will appear as warnings (![](../assets/images/NewButtons/warning.png)), since they clearly represent a problem, while others will be shown only as informational messages (![](../assets/images/NewButtons/button-info.png)).

Two different type of checks are conducted:

1. Consistency Checks: LEAP looks for common errors such as (a) whether all of the fuels specified in your demand analysis are produced in your Transformation analysis; (b) whether your Transformation analysis is producing fuels for which there are no requirements, (c) whether Transformation modules are incorrectly ordered (for example if Transmission and Distribution is placed below Electric Generation), and (d) whether Demand branches are not fully defined.
2. Check sum Validation: If you enter check sums for the level of final demand or primary requirements for fuels on the [Calculation Checksums](../16%20-%20Supporting%20Screens/Calculation_Checksums.md) screen, LEAP will validate that its calculated demand and primary requirements match those check sums. Deviations from those check sums will be reported in the Diagnostics screen.

Use the Diagnostics messages to interactively debug your analysis. Double-click on a message to switch back to the [Analysis View](Data_View.md) with the cursor placed on the relevant tree branch.