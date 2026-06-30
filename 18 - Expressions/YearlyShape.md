---
Source: https://leap.sei.org/help24/Expressions/YearlyShape.htm
---

# YearlyShape

## Syntax

YearlyShape(ShapeName)   
YearlyShape(BaseYearShapeName, EndYearShapeName)    
YearlyShape(BaseYearShapeName, LastHistoricalYearShapeName EndYearShapeName)

## Description

The YearlyShape function  specifies the seasonal and time of day variation in a variable within a single year.  Typically it is used to specify load shapes for a given electric device or for an electric system as a whole.  The function requires 1,2 or 3 parameters: the names of shapes to be applied  in all years or shapes to be applied in the base year, the last historical year and the end year.  If using 2 or 3 different parameters, LEAP will linearly interpolate between years to calculate the shapes in intervening years.

When specifying a yearly shape in a non-Current Accounts scenario using a single parameter, this parameter will be interpreted as the yearly shape for the end year.  LEAP will then linearly interpolate from the yearly shape that was specified in Current Accounts for the Last Historical Year to calculate the shapes in the intervening years in the scenario.

The yearly shapes names are used to refer to items in the Yearly Shapes library, which can be accessed in the General: [Yearly Shapes](../16%20-%20Supporting%20Screens/Load_Shapes.md) screen.

Each yearly shape specifies how a value will vary within a single year based on the time slices into which that year has been divided.  See the [General: Time Slices](../16%20-%20Supporting%20Screens/Time_Slices.md) screen to see the list of time slices for a given area.

Only some variables are time-sliced.  These include the [System Load Shape](../06%20-%20Load%20Shapes/System_Load_Shape.md) variable under the high-level Load Shapes category branch, the Transformation variables: [Merit Order](../08%20-%20Transformation/Merit_Order.md) and [Maximum Availability](../08%20-%20Transformation/Maxiumum_Capacity_Factor.md). and the demand-side [Load Shape](../05%20-%20Demand/Load_Shape.md) variable (which are visible only when the System Load Shape variable is set to [ShapeFromDemand](ShapeFromDemand.md)).  Attempting to use the YearlyShape function for variables that are not time sliced will generate an error message.

## Example

YearlyShape(Load Duration Curve, flat)  
  
This expression specifies a base year (2000) load shape named "Load Duration Curve" and an end year (2030) load shape named "Flat".  LEAP calculates the load shapes in the intervening years by linear interpolation for each time slice value.  The screen shot on the right shows the resulting load shapes for years 2000, 2010, 2020, and 2030.  Data for these two named load shapes are entered in the General: [Yearly Shapes](../16%20-%20Supporting%20Screens/Load_Shapes.md) screen.  The time slices (the hours that are common to all load shapes in an area) are specified in the [General: Time Slices](../16%20-%20Supporting%20Screens/Time_Slices.md) screen.