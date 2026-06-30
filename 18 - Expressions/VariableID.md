---
Source: https://leap.sei.org/help24/Expressions/VariableID.htm
---

# VariableID

## Syntax

VariableID(Branch:Variable) or  
VariableID(Name)

## Summary

Returns the unique variable ID associated with the specified branch:variable reference or with the specified name.  Names can be those of either the built-in variables (such as "Activity Level"  or "Final Energy Intensity") or the names of additional user-defined variables. This function can be useful when you need to pass information about the LEAP tree structure to an external script or DLL.

## Example

VariableID(Demand\Household\Refrigeration:Final Energy Intensity) = 2040 (the ID of the final energy intensity variable)  
VariableID(Demand\Household\Refrigeration:Activity Level) = 2027 (the ID of the activity level variable)  
VariableID(My User Variable) = the ID of the added user variable named "My User Variable"