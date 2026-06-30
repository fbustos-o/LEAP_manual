---
Source: https://leap.sei.org/help24/Expressions/Remainder.htm
---

# Remainder

## Syntax

Remainder(ExpressionA mathematical formula used to specify how the values of a variable changes from year to year. )

## Description

Calculates the remainder between an Expression and the sum of the values of neighboring (sibling) branches. The parameter specifies the total to which all neighboring branches should sum.  In other words, the function is calculated as Expression - Sum of Other Neighboring Branches.

## Tips

* An easy way to use this function is using the Remainder option accessed from orange ![](../assets/images/NewButtons/Exp%20Button.png) button attached to each expression.
* An error will occur if you attempt to use the remainder function in more than one neighboring branches.

## Examples

Consider two neighboring branches in a demand tree in which you are specifying the changing market share of Kerosene and LPG cooking technologies (in percent):

|  |  |
| --- | --- |
| Branch | Expression |
| Household\Cooking\Kerosene | Interpolate(2000, 50, 2020, 30) |
| Household\Cooking\LPG | Remainder(100) |

Remainder(100) is evaluated as follows:

2000 = 50.0  
2010 = 60.0  
2020 = 70.0