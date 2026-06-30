---
Source: https://leap.sei.org/help24/Expressions/GrowthAs.htm
---

# GrowthAs

## Syntax

GrowthAs(Branch:Variable) or  
GrowthAs(Branch:Variable, Elasticity) or

## Summary

Calculates a value in any given year using the previous value of the current branchAn item on the tree. Different types of branches are represented by different icons on the tree and the rate of growth in another named branch. This is equivalent to the formula:

Current Value(t) = Current Value(t-1) * NamedBranchValue(t)  
                                     NamedBranchValue(t-1)

In the second form of the function, the calculated growth rate is adjusted to reflect an elasticity. More precisely, the change in the current (dependent) branch is related to the change in the named branch raised to the power of the elasticity. This is a common approach in energy modeling, in which the growth in one variableData that can change over time. is estimated as a function of the growth in another (independent) variable.

When used within a time-series function such as Step or Interp, GrowthAs calculates a value for a particular year by applying the specified growth rate to value of the last explicitly entered yearly parameter.  Note that when used within a time-series function the function is limited to using only a single growth rate parameter.  The more complex multi-period forms of the function are not supported within time-series function.

## Examples

GrowthAs(Household\Rural)

Growth(GDP, 1)

In this example (elasticity = 1), the current branch grows at the same rate as the named branch (GNP).

GrowthAs(GDP, 0.9)

In this example (elasticity = 0.9), the current branch grows more slowly than GNP.

GrowthAs(GDP, 1.2)

In this example (elasticity = 1.2), the current branch grows more rapidly than GNP.

GrowthAs(GDP, 0)

In this example (elasticity = 0), the current branch is constant (i.e. independent of GNP).