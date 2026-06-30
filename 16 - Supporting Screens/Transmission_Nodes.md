---
Source: https://leap.sei.org/help24/Supporting_Screens/Transmission_Nodes.htm
---

# Transmission Nodes

See also: [Transmission Lines](Transmission_Lines.md)

![](../assets/images/NewScreens/TranNodes.png)

## Introduction

Use the Transmission Nodes screen to create a list of nodes (points) from which or to which energy will flow as part of your transmission network modeling.  Later, you can create a list of [Transmission lines](Transmission_Lines.md) that connect between pairs of nodes.

## Using the Transmission Nodes Screen

The Transmission Lines and Nodes screens are only available if you have installed NEMO and if you have enabled **Transmission Network** modeling on the [Settings: Optimization](Basic_Parameters_Screen.md#Optimization) screen. Currently, Transmission network modeling is only available for multi-region LEAP models.

Use the Add (![](../assets/images/NewButtons/Add.png)), Delete (![](../assets/images/NewButtons/Delete.png)) and edit  (![](../assets/images/NewButtons/rename.png)) buttons to manage the list of nodes.  The Nodes screen will automatically display your node on a map in the bottom-right corner of your screen.  Use the up (![](../assets/images/NewButtons/Arrow-up.png)) and down (![](../assets/images/NewButtons/Arrow-down.png)) buttons to change the display order of the nodes. Note though that this has no effect on calculated results. You can also use two filters to show nodes by fuel or by region.

When adding a node, you will be prompted to enter its name, region, fuel, and address in the Add Nodes dialog shown below.  LEAP will attempt to automatically look up the node's latitude and longitude (the position of the node) based on the address you enter. You can also enter notes to document your assumptions. Note that you cannot edit latitude and longitude values directly on the nodes screen. You must use the add/edit dialog to edit these properties.

![](../assets/images/NewScreens/AddNode.png)