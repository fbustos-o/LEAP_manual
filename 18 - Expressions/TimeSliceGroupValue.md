---
Source: https://leap.sei.org/help24/Expressions/TimeSliceGroupValue.htm
---

# TimeSliceGroupValue

## Syntax

TimeSliceGroupValue(SliceGroupName1, Value1, SliceGroupName2, Value2,..., ElseValue)

## Summary

Specifies a yearly shape by individually specifying the values associated with groups of seasonal or time of day time slices.  See the [General: Time Slices](../16%20-%20Supporting%20Screens/Time_Slices.md) screen to see the list of time slices defined in the area.  Note that slices (e.g. "January, weekend day") may be grouped together (e.g. "winter") typically by season or by month.  Use the ElseValue to specify the value that will be used for any groups not specifically named as parameters.

Only some variables are time-sliced.  These include the Transformation variables: [Merit Order](../08%20-%20Transformation/Merit_Order.md), System Peak Load Shape and [Maximum Availability](../08%20-%20Transformation/Maxiumum_Capacity_Factor.md). and the Demand Load Shape variable.  Attempting to use the TimeSliceGroupValue function for variables that are not time sliced will generate an error message.

## Example

TimeSliceGroupValue(Summer, 2, Spring, 4, 1)   This example assumes that time slice groups are defined for each of four seasons. This returns 2.0 for Summer, 4.0 for Spring and 1.0 for all other seasons.