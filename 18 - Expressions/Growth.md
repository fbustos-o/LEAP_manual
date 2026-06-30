---
Source: https://leap.sei.org/help24/Expressions/Growth.htm
---

# Growth

## Syntax

Growth(ExpressionA mathematical formula used to specify how the values of a variable changes from year to year. ) or  
Growth(Expression1, Year2, Expression2) or  
Growth(Expression1, Year2, Expression2, Year3, Expression3) or  
Growth(Expression1, Year2, Expression2, Year3, Expression3, Year4, Expression4) or  
Growth(Expression1, Year2, Expression2, Year3, Expression3, Year4, Expression4, Year5, Expression5)

## Description

Calculates a value in any given year using a growth rate from the base yearThe first historical year of a LEAP analysis. value. Because it references the base year value, this function is generally only available when editing scenarios. You can specify a single growth rate or using the alternative syntax, you can specify up to 5 periods with different growth rates. For example, from Year2 onwards the growth rate will be Expression2 and from Year3 onwards the growth rate will be Expression3. Specify decreases using negative values for the growth rate.

When used within a time-series function such as Step or Interp, Growth calculates a value for a particular year by applying the specified growth rate to value of the last explicitly entered yearly parameter.  Note that when used within a time-series function the function is limited to using only a single growth rate parameter.  The more complex multi-period forms of the function are not supported within time-series functions.

## Example

Growth(0.05) or Growth(5%)

This expression, entered in a scenario, causes the variable to grow at 5% per year through all of the scenario years, starting from the value in the year before the first scenario year.

Consider a case with an area where the Base Year is 2000 and the base year variable value is set of 100.  In this case the above expression yields the following results:

2001 = 105.00  
2002 = 110.25

NB: Take care when applying a growth rate over a long period as values can grow very large!

Growth(5%, 2015, 2%)

In this example, the variable again initially grows at 5% per year.  However, from 2015 onwards the variable grows at only 2% per year.