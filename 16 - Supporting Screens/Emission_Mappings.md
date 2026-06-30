---
Source: https://leap.sei.org/help24/Supporting_Screens/Emission_Mappings.htm
---

# Geographic Mapping

Menu Option: General: Geographic Mapping

![](../assets/images/NewScreens/Geographic%20Mapping.png)

## Introduction

Use this screen to create a named list of geographic mappings: raster (grid)-based GIS data sets, which can later used to allocate emissions to grid squares and then displayed on interactive maps in [Results View](../02%20-%20Views/Results_Screen.md) via the Gridded Map chart type.

## Using the Geographic Mapping Screen

Create a name for each mapping (which later will be used in LEAP's geographic allocation expressions)  and select an associated GIS data file containing a layer of raster data.  LEAP can make use of many different GIS file formats including GeoTIFF (GTIFF), ESRI ASCII (ASC), ESRI Binary (BIN), Multiresolution Seamless Image Database (MrSID), as well as GIF, JPEG, STDS and PAUX files. Support for NetCDF (NC) files is planned in a later version.  Each raster file should cover an area of equal or larger size than the shapes used for each region in your area.  These shapes are specified either in the regions screen (for multi regional areas) or in the Setup screen (for a single region area). Selected data sets can be of different resolutions and have different X/Y corner locations from each other, since LEAP will automatically re-scale, clip and normalize the data sets to a common resolution for use in allocating energy and emissions results to the common grid used in the Results View.  You can set the common resolution (cell size) used in LEAP's maps on the mapping tab of the General: [Settings](Basic_Parameters_Screen.md#Mapping) screen.

The top area of the screen displays a list of the mappings you have set up and shows additional information such as the file size (in KB) the file type, the cell size and the number of rows and columns in each raster data set.  It also shows the number of times each data set is referenced by expressions for the [Geography](../05%20-%20Demand/Geography.md) variable in your LEAP data set (primarily via the [Allocate](../18%20-%20Expressions/Allocate.md) function.  Additional information about each mapping data set such as the projection and data type are displayed in the Grid Information panel below the list of mappings.  You can also add your own notes to describe and document each data set in the Notes panel.

The Rebuild button (![](../assets/images/NewButtons/Refresh.png)) is used to regenerate the complete set of re-scaled, clipped and normalized GIS data used in LEAP's calculations. When rebuilding, LEAP will scan each raster map, overlaying it with the shape of each region in your area. Mappings that have no references in a LEAP data set will not be processed. Use the Add (![](../assets/images/NewButtons/Add.png)) button to add a new mapping and the Delete button (**![](../assets/images/NewButtons/Delete.png)**) to delete a mapping. You can also reorder the list using the Up (![](../assets/images/NewButtons/Arrow-up.png)) and Down (![](../assets/images/NewButtons/Arrow-down.png)) buttons. Use the Export to Excel (**![](../assets/images/NewButtons/MS-Excel.png)**) button to export the groupings to an Excel spreadsheet.

## Limitations

Due to limited use of memory in 32-bit applications, the 32-bit version of LEAP is restricted to creating and displaying maps with up to 50 by 50 cells.  The 64-bit version can  create and display maps with up to 300 x 300 cells. To keep the number of cells within these limits you may need to adjust the cell size settings via the mapping tab of the General: [Settings](Basic_Parameters_Screen.md#Mapping) screen.

## Finding Data Sets to Use in Your LEAP Analyses

A wide range of GIS maps are available from many different providers containing many different socioeconomic indicators.   A few examples of these include:

* [SEDAC](https://sedac.ciesin.columbia.edu/data/sets/browse): SEDAC, the NASA Socioeconomic Data and Applications Center hosts a wide range of GIS data focusing on human interactions with the environment.
* [ESRI Data & Maps](http://links.esri.com/ESRIdatamapsgroups): ESRI data includes many layers for the world, such as country boundaries, UTM zones, water, roads, railroads, airports, major cities, topography/bathymetry, and a nighttime view.
* [World Resources Institute](http://datasets.wri.org/): WRI hosts GIS data on power plant locations, population, poverty, agriculture, land cover & land form, forests and many other topics.
* [United Nations Environment Programme Data Explorer](http://geodata.grid.unep.ch/): UNEP is a source for data sets used by UNEP and its partners in the Global Environment Outlook (GEO) report and other integrated environment assessments. Its online database holds more than 500 different variables as national, sub-regional, regional and global statistics or as geospatial data sets (maps), covering themes like freshwater, population, forests, emissions, climate, disasters, health and GDP.
* MIT also [maintains a list](https://libguides.mit.edu/gis/world) of additional GIS data sources.