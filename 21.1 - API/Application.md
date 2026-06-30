---
Source: https://leap.sei.org/help24/API/Application.htm
---

# Application API

See also: [Automating LEAP with the API](API.md)

The LEAPApplication class contains top-level
properties and methods, including access to all other classes.

Note: in the following examples, a reference
to LEAP, as in LEAP.ActiveArea, assumes that there is an object named
LEAP of class LEAPApplication. This can be created in VBScript by entering:

SET LEAP
= CreateObject("LEAP.LEAPApplication").    
  
However, this is not necessary when running scripts inside LEAP (e.g. from
the script editor) since an object named LEAP implicitly exists whenever
LEAP is running.

Please
use the [Script Editor](Using_the_Script_Editor.md) for documentation
of the properties and methods of the Application API. The right-hand pane
of the Script editor fully enumerates all collections and objects in the
LEAP API.