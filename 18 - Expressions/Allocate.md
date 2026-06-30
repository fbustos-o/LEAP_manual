---
Source: https://leap.sei.org/help24/Expressions/Allocate.htm
---

# Allocate

**See also:** [AllocateEvenly](AllocateEvenly.md), [AllocateNone](AllocateNone.md)

## Syntax

Allocate(Mapping1) or  
Allocate(Mapping1, Mapping2) or  
Allocate(Mapping1, Mapping2, Mapping3)

## Summary

Allocates the values at a given branch among the map squares within the shape of the current area (in a one region data set) or among the map squares of the shape for the current region (in a multi-region area). Values are allocated in proportion to the values contained in the named geographic mapping.  Geographic mappings are set up and named in the General: [Geographic Mapping](../16%20-%20Supporting%20Screens/Emission_Mappings.md) screen.  Typically each mapping is based on a single raster map containing socioeconomic data set for variables such as the population residing within each grid square.  You can use a variety of file formats for these data sets such as GeoTiff (GTIF), NetCDF and ESRI ASCII Grid formats.

When two mappings are specified, LEAP will linearly interpolate between the values in the two mappings for each corresponding grid square, assuming the first mapping contains base year values and the second mapping contains end year values.

When three mappings are specified, LEAP will linearly interpolate between the values in the three mappings for each corresponding grid square, assuming the first mapping contains base year values, the second mapping contains values for the last historical year (the year before the first scenario year) and the third mapping contains end year values.

Use in conjunction with the [gridded maps](../02%20-%20Views/Showing_Gridded_Maps_in_Results_View.md) shown in Results View.  This function can only be used in conjunction with the [Geography](../05%20-%20Demand/Geography.md) variable.

## Example

Allocate(Population) allocates values in proportion to the data in the "population" mapping.