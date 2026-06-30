---
Source: https://leap.sei.org/help24/Maps/MapWinGIS.htm
---

# MapWinGIS

See also: [Results View](../02%20-%20Views/Results_Screen.md), [Using Maps](../02%20-%20Views/Maps.md)

Before showing maps in LEAP or using the optional [Map Results to Grid](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) feature, you must first install the open source MapWinGIS components.  MapWinGIS must be downloaded separately from LEAP (see below).

MapWinGIS is a free and open source geographic information system (GIS) ActiveX Control and Application Programming Interface (API) supporting both 32-bit and 64-bit Windows. MapWinGIS can be easily installed and integrated with LEAP. It is made available under the MPL 2.0 open source license, meaning that it can be freely used in both commercial and non-commercial applications.  Aside from providing GIS mapping capabilities, MapWinGIS also provides access to the GDAL library of routines, which are used in LEAP for re-scaling and cropping GIS data sets for use in LEAP's grid mapping features.

LEAP requires MapWinGIS version 5.0.2 or later.

You can download MapWinGIS from this page: <https://github.com/MapWindow/MapWinGIS/releases/latest>

At the time of writing, recommended versions of MapWinGIS is:

* [64-bit MapWinGIS.](https://github.com/MapWindow/MapWinGIS/releases/download/v5.1.1.1/MapWinGIS-only-v5.1.1.1-x64-VS2017.exe)

We recommend installing MapWinGIS in the default folder suggested by the installation program, but LEAP does not require it to be installed in any particular folder.  Once installed, you should reboot your PC before re-running LEAP.

In LEAP, check the Help: About screen to see if LEAP properly recognized MapWinGIS.  If LEAP has trouble recognizing MapWinGIS, this may be due to insufficient access rights on your PC preventing the components being properly registered with Windows.  You can manually register the components by running the RegMapWinGIS.cmd command file located in the folder where MapWinGIS is installed.  Make sure to run this command with Windows Administrator rights.

Special thanks to [Paul Meems](https://github.com/pmeems), the lead developer of MapWinGIS, for his help with integrating MapWinGIS and LEAP.