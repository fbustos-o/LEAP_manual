---
Source: https://leap.sei.org/help24/API/Area.htm
---

# Areas API

See also: [Automating LEAP with the API](API.md), [Manage Areas](../16%20-%20Supporting%20Screens/Area_Manager.md)

The LEAPArea class represents a single LEAP area (a data set), whereas LEAPAreas is the collection of all areas on your PC .  The Areas collection is also a property of the [LEAPApplication](Application.md) class.  You can get access to an Area in two different ways:

1. LEAP.Areas(AreaName or Index), specifying either the name of the area or a number from 1 to LEAP.Areas.Count, e.g., LEAP.Areas("Freedonia") or LEAP.Areas(1)
2. LEAP.ActiveArea

Please use the [Script Editor](Using_the_Script_Editor.md) for documentation of the properties and methods of the Areas API. The right-hand pane of the Script editor fully enumerates all collections and objects in the LEAP API.