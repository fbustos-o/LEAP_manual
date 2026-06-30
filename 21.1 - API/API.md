---
Source: https://leap.sei.org/help24/API/API.htm
---

# the Application Programming Interface (API)

See also: [Exploring the API with Excel](Exploring.md),  [The Script Editor](Using_the_Script_Editor.md)

LEAP can act as a standard "COM Automation Server," meaning that other Windows programs can control LEAP directly: changing data values, calculating results, and exporting them to Excel or other applications.  The API even provides functions for examining or changing LEAP's data structures  This ability to program LEAP can be very powerful. For example, you could write a short script that could run LEAP calculations many times, each time with a different set of input assumption.  LEAP's results could then be output to Excel or processed in the script and used to calculate revised assumptions for subsequent LEAP calculations.  In this way LEAP's basic accounting calculations could be coupled with more sophisticated algorithms such as goal-seeking or optimizing algorithms.

The LEAP Application Programming Interface (API) consists of several "classes," each with their own "properties" and "methods." Properties are values that can be inspected or changed, whereas methods are functions can be called do something.

The following classes are defined in LEAP's API:

* [LEAPApplication](Application.md): top-level properties and methods, including access to all other classes.
* [LEAPArea](Area.md): a LEAP area.  
  [LEAPAreas](Area.md): collection of all LEAP areas.
* [LEAPBranch](Branch.md): a specific branch on the data tree (e.g., \Demand\Household\Urban).  
  [LEAPBranches](Branch.md): a collection of all the child branches for a specified branch (e.g., Branch("\Demand").Children ).
* [LEAPFavorite](Favorites_API.md): a named favorite result chart.  
  [LEAPFavorites:](Favorites_API.md) the collection of all favorites in the active area.
* [LEAPFuel](Fuels_API.md): a specific fuel in the active area.  
  [LEAPFuels](Fuels_API.md): the collection of all fuels in the active area.
* [LEAPRegion](Regions_API.md): a specific region in the active area.  
  [LEAPRegions](Regions_API.md): the collection of all regions in the active area.
* [LEAPScenario](Scenario.md): a scenario in the active area.  
  [LEAPScenarios](Scenario.md): the collection of all scenarios in the active area.
* [LEAPUnit](Units_API.md): a specific unit region in the active area.  
  [LEAPUnits](Units_API.md): the collection of all units in the active area.
* [LEAPVariable](Variable.md): a Variable for a given Branch (e.g., "Activity Level"  for Branch \Demand\Households\Urban).  
  [LEAPVariables](Variable.md): collection of all Variables for a single Branch (e.g., all variables for \Demand\Households\Urban).
* [LEAPView](Views_API.md): a view of the LEAP area.  
  [LEAPViews](Views_API.md): a collection of all views.

LEAP has its own built-in [script editor](Using_the_Script_Editor.md) that can be used to edit, interactively debug and run scripts that automate LEAP using its API.  LEAP uses Microsoft's Windows Script (aka ActiveScript) technology and directly supports scripts written in VBScript.  Some other web-based resources you may find useful:

* [Windows Script Information](http://msdn2.microsoft.com/en-us/library/ms950396)
* [A VBScript tutorial](https://www.tutorialspoint.com/vbscript/index.htm)
* [A VBScript reference guide](https://www.w3schools.com/asp/asp_ref_vbscript_functions.asp)