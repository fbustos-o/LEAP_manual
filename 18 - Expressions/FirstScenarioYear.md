---
Source: https://leap.sei.org/help24/Expressions/FirstScenarioYear.htm
---

# FirstScenarioYear

## Syntax

FirstScenarioYear

## Description

This function returns the year of the First Scenario Year.

In some cases you might want to specify a time-series of historical data in Current Accounts (e.g. using an [Interp](Interp.md) function) and then have the scenarios start in a later year.  For example imagine you have historical data for 1980-2000 and you then want the scenarios all to run from 2001-2030.  In this situation, you can specify a variable called First Scenario Year on the General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md): Years screen.  You can then reference this value in your expressions using this function.

Note: previous versions of LEAP allowed you to write this function as "FSY".  This is no longer supported.