---
Source: https://leap.sei.org/help24/Expressions/SourceBelow.htm
---

# SourceBelow

## Syntax

SourceBelow

## Description

This function indicates that the source module for an input [feedstock fuel](../08%20-%20Transformation/Feedstock_Fuel_Shares.md) or [auxiliary fuel](../08%20-%20Transformation/Auxiliary_Fuel_Use.md) of a Transformation module is a module lower down in the list than the current module.  Ultimately, if no modules below the current module produce that fuel, then LEAP will attempt to supply the fuel from either indigenous production or from imports. This function is only relevant to the [Fuel Source](../08%20-%20Transformation/Fuel_Source.md) variable which is only visible for feedstock fuels and auxiliary fuels when editing a scenario using the Full Energy System Optimization methodology.  SourceBelow is the default value for the Fuel Source variable.  For finer-grained control, use the [SourceModule](Source_Module.md) function to specify the module that produces the input fuel.