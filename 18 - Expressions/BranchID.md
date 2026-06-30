---
Source: https://leap.sei.org/help24/Expressions/BranchID.htm
---

# BranchID

## Syntax

BranchID, or  
BranchID(Branch:Variable)

## Summary

Returns the unique branch ID associated with either the current branch or the specified branch:variable reference.  This function can be useful when you need to pass information about the LEAP tree structure to an external script or DLL.

## Example

BranchID(Demand\Household\Refrigeration:Final Energy Intensity) = 39 (the ID of the referenced branch)