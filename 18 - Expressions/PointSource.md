---
Source: https://leap.sei.org/help24/Expressions/PointSource.htm
---

# PointSource

## Syntax

PointSource(Latitude, Longitude),
or  
PointSource(Latitude, Longitude, Elevation)

## Summary

Allocates all values at
a given branch to the map square containing the specified location specified
in terms of latitude and longitude.  Note that elevation can also
be specified in meters but is not currently utilized in LEAP's calculations.
It is important to ensure that the point specified by the function's parameters
are located within the shape of the current area (in a one region data
set) or among the map squares of the shape for the current region (in
a multi-region area).

Use in conjunction with
the [gridded
maps](../02%20-%20Views/Showing_Gridded_Maps_in_Results_View.md) shown in Results View.  This function can only be used in
conjunction with the [Geography](../05%20-%20Demand/Geography.md) variable.

Latitude values range from -90 (the South
Pole) to zero (the Equator) to +90 (the North Pole).  Longitude values
range from -180 (west) to +180 (east), with 0 being the Greenwich Meridian
and +/-180 being the international dateline. Refer to [Wikipedia](https://en.wikipedia.org/)
for more information on [latitude](https://en.wikipedia.org/wiki/Latitude)
and [longitude](https://en.wikipedia.org/wiki/Longitude) values.

Example:

PointSource(27.858, 91.012)