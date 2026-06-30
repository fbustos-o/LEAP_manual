---
Source: https://leap.sei.org/help24/Demand/Load_Shape.htm
---

# Load Shape

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md), [Final Energy Intensity](Final_Energy_Intensity.md)

The load shape variable is used to specify the seasonal and time-of-day variation in the energy consumption for particular demand technologies.  Data for a load shape vary among the time slices into which each year is divided.  Time slices are defined on the [General: Time Slices](../16%20-%20Supporting%20Screens/Time_Slices.md) screen,

The load shape variable is only visible if two conditions are true:

1. You have chosen to include load shapes in your analysis for particular fuels.  You can do this on the [General: Scope & Scale](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) screen, and,

2. Under the high level Load Shapes branch, you have set the [System Load Shape](../06%20-%20Load%20Shapes/System_Load_Shape.md) variable to the [ShapeFromDemand](../18%20-%20Expressions/ShapeFromDemand.md) method.

## Entering Load Shape Data

You can specify demand load shape data in a variety of ways:

* Select a predefined yearly shape from the [Yearly Shapes](../16%20-%20Supporting%20Screens/Load_Shapes.md) library.  You can do this by clicking the orange button (![](../assets/images/NewButtons/Exp%20Button.png)) attached to each expression and then selecting one of the yearly shapes listed (![](../assets/images/NewButtons/YearlyShapes..png)).  The result will be that LEAP will write a [YearlyShape](../18%20-%20Expressions/YearlyShape.md) expression that references the named yearly shape.
* Use one of the preset yearly shapes using the [ShapeFlat](../18%20-%20Expressions/ShapeFlat.md), [ShapeNone](../18%20-%20Expressions/ShapeNone.md), or [ShapeDefault](../18%20-%20Expressions/ShapeDefault.md) functions.
* Explicitly enter time-sliced information directly for the Load Shape variable.  You can do this by using the [TimeSliceValue](../18%20-%20Expressions/TimeSliceValue.md) and [TimeSliceGroupValue](../18%20-%20Expressions/TimeSliceGroupValue.md) functions.