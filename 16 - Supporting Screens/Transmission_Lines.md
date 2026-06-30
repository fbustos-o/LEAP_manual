---
Source: https://leap.sei.org/help24/Supporting_Screens/Transmission_Lines.htm
---

# Transmission Lines

See also: [Transmission Nodes](Transmission_Nodes.md)

![](../assets/images/NewScreens/TranLines.png)

## Introduction

Use the Transmission Lines  screen to create links between pairs of [nodes](Transmission_Nodes.md). These lines are the basis for transmission network modeling.

Energy can flow in either direction through a transmission line and flows may go in both directions over the course of a single year depending on the cost and availability of energy supplies in each region (and the amount of energy storage in each region).  By convention, energy flows are displayed as positive values when they flow from the **From** node to the **To** node of each line. Energy flows are shown as negative values when they  flow in the reverse direction.  To avoid confusion in interpreting results, LEAP requires that the from/to node ordering must be the same for all lines connecting the same regions.  For example, you cannot have one line from England to France and another from France to England.

## Using the Transmission Lines Screen

The Transmission Lines and Nodes screens are only available if you have installed NEMO, and if you have enabled **Transmission Network** modeling on the [Settings: Optimization](Basic_Parameters_Screen.md#Optimization) screen. Currently, Transmission network modeling is only available for multi-region LEAP models.

Use the Add (![](../assets/images/NewButtons/Add.png)) and Delete (![](../assets/images/NewButtons/Delete.png)) buttons to manage the list of lines.  The lines screen will automatically display your lines on a map in the bottom-right corner of your screen.  You can also use a filter to show lines using particular fuels.

After adding a line, you will be shown the regions being connected (from, to) and the straight line distance between the two connected nodes.  You can enter the actual distance yourself, which must be greater than or equal to the straight line distance.  Actual distance values can be used later if you wish to specify line losses per km of line.

Later you will specify various technical data describing each line as part of LEAP's transmission network modeling.  This data includes characteristics such as [construction year](../09%20-%20Transmission%20Modeling/Construction_Year.md), [losses](../09%20-%20Transmission%20Modeling/Losses.md), [maximum availability](../09%20-%20Transmission%20Modeling/Transmission_Availability.md), [capital costs](../09%20-%20Transmission%20Modeling/Capital_Cost.md), [fixed](../09%20-%20Transmission%20Modeling/Fixed_OM_Cost.md) and [variable O&M](../09%20-%20Transmission%20Modeling/Variable_OM_Cost.md) costs, etc.

Tip: you can specify if a line is enabled using the check box on the far right of the data entry table.  Any lines that are not enabled will not appear in the LEAP tree and will not be included in LEAP's transmission network modeling.  Use the enabled property if you want to temporarily exclude certain lines from your analysis.