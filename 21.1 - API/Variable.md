---
Source: https://leap.sei.org/help24/API/Variable.htm
---

# Variables API

See
also: [Automating LEAP with the API](API.md),

The LEAPVariable class represents a Variable for a single Branch, whereas
LEAPVariables is a collection of all valid Variables for a given Branch.

You can get access to a LEAPVariable from the Variables collection:

LEAPVariables(VariableName
or Index), specifying either the name of the variable or a number from
1 to LEAPVariables.Count, e.g., LEAP.Branch("Demand\Househods").Variables("Activity
Level") or LEAP.Branch("Demand\Househods").Variables(1)

Please use the [Script
Editor](Using_the_Script_Editor.md) for documentation of the properties and methods of the Variables
API. The right-hand pane of the Script editor fully enumerates all collections
and objects in the LEAP API.