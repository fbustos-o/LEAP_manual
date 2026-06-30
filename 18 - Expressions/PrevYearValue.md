---
Source: https://leap.sei.org/help24/Expressions/PrevYearValue.htm
---

# PrevYearValue

## Syntax

PrevYearValue or  
PrevYearValue(Branch:Variable)

## Summary

Calculates the previous year's value of either the current branchAn item on the tree. Different types of branches are represented by different icons on the tree or of another branch referred to as a parameter to the function. This function is not generally available when entering Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year..

When used within a time-series function such as Step or Interp, PrevYearValue returns the value of the last explicitly entered yearly parameter.

## Examples

10+PrevYearValue

Evaluated for a value of 100 in 2000

2001 = 110  
2002 = 120  
2003 = 130

0.3+PrevYearValue(Households\Urban\Cooking)

Evaluated for a value of 30 in 2000 in a branch named "Household\Urban\Cooking".

2001 = 30.3  
2002 = 30.6  
2003 = 30.9