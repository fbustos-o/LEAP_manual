---
Source: https://leap.sei.org/help24/Expressions/If.htm
---

# IF

## Syntax

IF(TestExpression1, ResultIfTrue1, TestExpression2, ResultIfTrue2, ..., TestExpressionN, ResultIfTrueN, ResultIfAllFalse)

See also: [Operators](Operators.md), [True](True.md), [False](False.md), [AND](AND.md), [OR](OR.md), [NOT](opNot.md)

## Summary

Use the If function to return a value depending on whether each TestExpression is [True](True.md) (<> 0) or [False](False.md) (=0).

Test expressions are typically made up of statements which are evaluated using LEAP's logical operators, such as "year <= 2010".

You can include any number of paired test expressions and result values, plus a single result values that is returned if all of the other test expressions are false.  The whole expression is evaluated from left to right, stopping at the point where a test expression evaluates as true.

In its simplest form the function may include just a single test expression as follows:

IF(TestExpression, ResultIfTrue, ResultIfFalse)

## Examples

If(Income > 1000, 10, 20)  
If the branch/variable named Income has a value greater than 1000 then the function evaluates to 10. Otherwise, is it 20.

If( year >= 2005, 30, 0)  
= 30 in years 2005 and after, 0 before 2005

If( year < 2005, 0, year < 2010, 10, year < 2020, 15, 20)  
= 0 in years before 2005, 10 in years 2005-2009, 15 in 2010-2019, and 20 in years 2020 and after.