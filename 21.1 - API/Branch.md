---
Source: https://leap.sei.org/help24/API/Branch.htm
---

# Branches API

See
also:
[Automating LEAP with the API](API.md)
 

The LEAPBranch class represents a specific
Branch on the data tree (e.g., Demand\Households\Urban ), whereas LEAPBranches
is a collection of all child Branches for a specified Branch (e.g., all
child branches of  Demand\Households).

A LEAPBranches collection comes from the Child
property of a LEAPBranch:

1. LEAPBranch.Children,
   e.g., LEAP.Branch("Demand\Households").Children

You can get access to a LEAPBranch in three
different ways:

1. LEAPApplication.Branch(FullBranchPath),
   e.g., LEAP.Branch("Demand\Households"
2. LEAPBranches(Index),
   specifying a number from 1 to LEAPBranches.Count, e.g., LEAP.Branch("Demand\Households").Children(1)
3. LEAP.Branch(BranchID),
   specifying the unique ID number of a branch.

Please
use the [Script Editor](Using_the_Script_Editor.md) for documentation
of the properties and methods of the Branches API. The right-hand pane
of the Script editor fully enumerates all collections and objects in the
LEAP API.