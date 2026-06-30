---
Source: https://leap.sei.org/help24/Expressions/ShapeFromDemand.htm
---

# ShapeFromDemand

## Syntax

ShapeFromDemand

## Description

Used when specifying the shape of the [System Load Shape](../06%20-%20Load%20Shapes/System_Load_Shape.md) variable for a particular fuel. Instructs LEAP to calculate the system load shape by summing the loads of each individual demand device that uses that fuel.  These demand-side yearly shapes are specified using the [Load Shape](../05%20-%20Demand/Load_Shape.md) variables specified at each demand technology branch (![](../assets/images/NewButtons/Tree/Technology.png)).

This function is entered for each fuel in the [System Load Shape](../06%20-%20Load%20Shapes/System_Load_Shape.md) variable specified for each fuel under the high level Load Shapes branch.