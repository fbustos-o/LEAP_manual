---
Source: https://leap.sei.org/help24/Expressions/TimeSliceValue.htm
---

# TimeSliceValue

## Syntax

TimeSliceValue(SliceName1, SliceValue1, SliceName2, SliceValue2,..., ElseValue)

## Summary

Specifies a yearly shape by individually specifying the values associated with different seasonal or time of day time slices.  See the [General: Time Slices](../16%20-%20Supporting%20Screens/Time_Slices.md) screen to see the list of time slices defined in the area.  Use the ElseValue to specify the value that will be used for any slices not specifically named as parameters.

Only some variables are time-sliced.  These include the Transformation variables: [Merit Order](../08%20-%20Transformation/Merit_Order.md), System Peak Load Shape and [Maximum Availability](../08%20-%20Transformation/Maxiumum_Capacity_Factor.md). and the Demand Load Shape variable.  Attempting to use the TimeSliceValue function for variables that are not time sliced will generate an error message.

## Example

TimeSliceValue(January, 2, February, 4, August, 3, 1)   This example assumes that time slices are defined for each month of the year. This returns 2.0 for January, 4.0 for February, 3.0 for August and 1.0 for all other months.