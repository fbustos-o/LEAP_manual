---
Source: https://leap.sei.org/help24/Expressions/Source_Module.htm
---

# SourceModule

## Syntax

SourceModule(ModuleName)

## Description

This expression indicates that a specific named module is the source for an input [feedstock fuel](../08%20-%20Transformation/Feedstock_Fuel_Shares.md) or [auxiliary fuel](../08%20-%20Transformation/Auxiliary_Fuel_Use.md) of a Transformation module.  Ultimately, if that module does not produce the fuel, then LEAP will attempt to supply the fuel from either indigenous production or from imports. This function is only relevant to the [Fuel Source](../08%20-%20Transformation/Fuel_Source.md) variable which is only visible for feedstock fuels and auxiliary fuels when editing a scenario using the Full Energy System Optimization methodology.  SourceBelow is the default value for the Fuel Source variable.

Use the orange  Exp button (![](../assets/images/NewButtons/Exp%20Button.png)) in the data entry table to quickly choose a module as a parameter to the SourceModule function.