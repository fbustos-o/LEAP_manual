---
Source: https://leap.sei.org/help24/Expressions/ScenarioIndicator.htm
---

# ScenarioIndicator

## Syntax

ScenarioIndicator(Branch:Variable, IndicatorFunction, YearMode) or  
ScenarioIndicator(Branch:Variable, IndicatorFunction)

## Summary

Calculates a cross-scenario indicator for the current branch and variable.

* [IndicatorFunction](IndicatorFunctions.md) is a parameter that tells LEAP what type of indicator to calculate.  LEAP can calculate many different indicators including rankings, scores and ratios.
* YearMode is a parameter indicating over which years the Indicator should be calculated.  It can have three value as follows:

yOne, yEach =  0: Indicates that the indicator should be calculated separately in each year in each scenario.  
yBase = 1: Indicates that the indicator should be calculated only once for the base year of the study.  
yAll = 2: Indicates that the indicator should be calculated once looking across all values in all years.

If the YearMode parameter is omitted from the function then LEAP assumes YearMode=yEach.

## Example

 ScenarioIndicator(GDP,fRankHigh)  Ranks scenarios from 1 to n (where n is the number of scenarios) based on which had the highest GDP.  The ranking is calculated separately in each year.