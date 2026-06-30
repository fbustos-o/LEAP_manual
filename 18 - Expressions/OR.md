---
Source: https://leap.sei.org/help24/Expressions/OR.htm
---

# Or Operator

## Syntax

Expression Or Expression

See also: [Operators](Operators.md), [IF](If.md), [True](True.md), [False](False.md), [And](AND.md), [Not](opNot.md), [Xor](opXOr.md)

## Summary

The Or operator returns [True](True.md) if either the left hand term or the right hand term are True.  Otherwise it returns [False](False.md).

## Examples

IF(2=3 Or 3=3, 10, 5) = 10  
IF(True Or False, 10, 5) = 10  
IF(False Or False, 10, 5) = 5