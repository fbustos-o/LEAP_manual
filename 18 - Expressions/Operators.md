---
Source: https://leap.sei.org/help24/Expressions/Operators.htm
---

# Expression Operators

LEAP supports all of the standard mathematical and logical operators in expressions as follows:

|  |  |
| --- | --- |
| Operator | Meaning |
| Arithmetical Operators | |
| + (Plus) | Adds the term on the left to the term on the right. |
| - (Minus) | Subtracts the term on the right from the term on the left. |
| * (Times) | Multiplies the term on the left by the term on the right. |
| / (Divide) | Divides the term on the left by the term on the right. An error will occur if the term on the right is zero. |
| ^ (Power) | Raises the term on the left to the power of the term on the right |
| Logical Operators | |
| =  ([Equal](Eq.md)) | Returns TRUE if the term on the left equals the term on the right: otherwise returns false. |
| <>  ([Not Equal](NotEq.md)) | Returns TRUE if the term on the left does not equal the term on the right: otherwise returns false. |
| <  ([Less Than](LT.md)) | Returns TRUE if the term on the left is less than the term on the right: otherwise returns false. |
| >  ([Greater Than](GT.md)) | Returns TRUE if the term on the left is greater than the term on the right: otherwise returns false. |
| <=  [(Less Than or Equal](LTEq.md)) | Returns TRUE if the term on the left is less than or equal to the term on the right: otherwise returns false. |
| >=  ([Greater Than or Equal](GTEq.md)) | Returns TRUE if the term on the left is greater than or equal to the term on the right: otherwise returns false. |
| And | Returns true if both the left hand term and the right hand term are TRUE. |
| Or | Returns true if either the left hand term or the right hand term are TRUE. |
| Not/Xor | Returns true if the left hand terms is true and right hand term is false, or if the right hand term is true and the left hand term is false. Xor is a synonym for Not. |

Notes: In LEAP, the term FALSE has the value zero (0), while TRUE has a value of one (1). However, in logical tests, any non-zero value is equivalent to TRUE. Logical operators are typically used in conjunction with the [If](If.md) function, to yield two alternative results depending on whether the result is true or false. For example: IF(Variable1 < Variable2, ValueIfTrue, ValueIfFalse).