---
Source: https://leap.sei.org/help24/Load_Shapes/System_Load_Shape.htm
---

# System Load Shape

See also:  [YearlyShape](../18%20-%20Expressions/YearlyShape.md), [ShapeNone](../18%20-%20Expressions/ShapeNone.md), [ShapeFlat](../18%20-%20Expressions/ShapeFlat.md), [ShapeDefault](../18%20-%20Expressions/ShapeDefault.md), [ShapeFromDemand](../18%20-%20Expressions/ShapeFromDemand.md)

If you have included Load Shapes as part of the scope of your analysis on the Settings: [Scope & Scale](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#LoadShapes) screen, then in Analysis View you will see a top-level category branch named Load Shapes sitting immediately after the top-level Demand category branch in the Analysis View tree. Under this branch, you will specify the  System Load Shapes (![](../assets/images/NewButtons/Tree/YearlyShape..png)) for each fuel specified on the [Settings: Scope & Scale](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen.

You can entrirely switch load shapes on or off via the [Settings: Scope](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) screen, from you which you can specify that load shaes are specified for all fuels or for selected fuels.  When you specify selected fuels, you can choose which fuels have load shapes via the **Has Load Shape** column of the General: [Fuels](../16%20-%20Supporting%20Screens/Fuels.md) screen.

Load shapes can either be **specified** **centrally** for a fuel using various expressions such as the [YearlyShape](../18%20-%20Expressions/YearlyShape.md) function or using standard shape functions such as [ShapeFlat](../18%20-%20Expressions/ShapeFlat.md) or [ShapeNone](../18%20-%20Expressions/ShapeNone.md).  You can also have load shapes be **calculated internally** based on the shape of the individual loads of each demand device using the [ShapeFromDemand](../18%20-%20Expressions/ShapeFromDemand.md) function. The easiest way to specify these functions is to select them by clicking on the orange expression button attached to each expression (![](../assets/images/NewButtons/Exp%20Button.png)).

If you use the ShapeFromDemand function, you will see an additional [Load Shape](../05%20-%20Demand/Load_Shape.md) variable displayed for each demand device using that fuel. Here you can specify the yearly load shape for each demand device (again, typically by using the [YearlyShape](../18%20-%20Expressions/YearlyShape.md) function to reference a load shape stored in the Yearly Shapes library).

You can use different load shape methods for each fuel. For example, you might use demand-side load shapes for electricity demands, and simpler centrally specified load shapes for all other fuels. Load shape methods can also differ among scenarios.  They can be entered as either a percentage of the peak load, or as a percentage of the annual energy load. LEAP supports both formats and will internally convert shapes as needed to a common format.