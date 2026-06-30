---
Source: https://leap.sei.org/help24/API/Units_API.htm
---

# Units API

See also: [Automating LEAP with the API](API.md), [Units](../16%20-%20Supporting%20Screens/Units.md)

The LEAPUnit class represents a single LEAP unit, whereas LEAPUnits is the collection of all units in the active area. The Units collection is a property of the [LEAPApplication](Application.md) class:

You can get access to a LEAPUnit from the Units collection:

1. LEAPUnits(UnitComment or Index), specifying either the comment associated with a unit or a number from 1 to LEAPApplication.Units.Count, e.g., LEAP.Units("Current Accounts") or LEAP.Units(1)

|  |  |
| --- | --- |
| LEAPUnits Properties and Methods | VBScript Example |
| Item(UnitComment or Index): Get the unit identified by comment or index (from 1 to Units.Count). If more than one unit has the same comment, then the latest unit is chosen. Read only.  Default property. | PRINT LEAP.Units.Item(1).Date  PRINT LEAP.Units(1).Date  Note: the Item property is the default property, and therefore is usually omitted. Thus, the two examples above are equivalent. |
| Count: Get the number of LEAP units in the active area. Read only. | FOR i = 1 to LEAP.Units.Count;    PRINT LEAP.Units(i).Name  NEXT |

|  |  |
| --- | --- |
| LEAPUnit Properties and Methods | VBScript Example |
| Name: Gets the long name of the unit.  Read only. Default property. | PRINT LEAP.Units(1).Name |
| Abbreviation: Gets the short abbreviation for the unit. Read only. |  |
| ConversionFactor:  Gets a string showing the conversion factor from the current unit to the default unit in the classs. Read only. |  |
| ID: Gets the unique numeric ID of the fuel.  This ID is used internally by LEAP.  It is not displayed in LEAP's normal interface but may be useful when automating LEAP.  Read only. |  |
| UnitClass: Gets a string indicating the unit class (energy, power, mass, volume, area, length, currency, etc.). Read only. |  |