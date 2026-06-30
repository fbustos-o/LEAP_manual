---
Source: https://leap.sei.org/help24/Expressions/RegionIndicator.htm
---

# RegionIndicator

## Syntax

RegionIndicator(Branch:Variable, IndicatorFunction, YearMode, RegionMode) or  
RegionIndicator(Branch:Variable, IndicatorFunction, YearMode) or  
RegionIndicator(Branch:Variable, IndicatorFunction) or

## Summary

Calculates a composite indicator for the current branch and variable by comparing across regions.

* [IndicatorFunction](IndicatorFunctions.md) is a parameter that tells LEAP what type of indicator to calculate.  LEAP can calculate many different indicators including rankings, scores and ratios.
* YearMode is a parameter indicating over which years the Indicator should be calculated.  It can have three value as follows:

yOne, yEach =  0: Indicates that the indicator should be calculated separately in each year in each scenario.  
yBase = 1: Indicates that the indicator should be calculated only once for the base year of the study.  
yAll = 2: Indicates that the indicator should be calculated once looking across all values in all years.

If the YearMode parameter is omitted from the function then LEAP assumes YearMode=yEach

* RegionMode is a parameter indicating over which regions the indicator should be calculated.  It can have two values as follows:

rAll = 0: Calculates the indicator across all regions.  
rCalculated = 1: Calculates the indicator across all regions marked for calculation in the [General: Regions](../16%20-%20Supporting%20Screens/Regions.md) screen.  Values for regions not marked for calculation are ignored.

## Example

RegionIndicator(GDP,fRankHigh)  Ranks regions from 1 to n (where n is the number of scenarios) based on which had the highest GDP.  The ranking is calculated separately in each year.