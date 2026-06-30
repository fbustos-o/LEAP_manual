---
Source: https://leap.sei.org/help24/API/Scenario.htm
---

# Scenarios API

See
also: [Automating LEAP with the API](API.md), [Manage
Scenarios](../16%20-%20Supporting%20Screens/Scenario_Manager.md)

The LEAPScenario class represents a single LEAP scenario, whereas LEAPScenarios
is the collection of all scenarios in the active area (including Current
Accounts).  The Scenarios collection is a property of the [LEAPApplication](Application.md)
class:

You can get access to a LEAPScenario in two different ways:

1. LEAPApplication.Scenarios(ScenarioName
   or Index), specifying either the name of the scenario or a number
   from 1 to LEAPApplication.Scenarios.Count, e.g., LEAP.Scenarios("Current
   Accounts") or LEAP.Scenarios(1)
2. LEAPApplication.ActiveScenario,
   e.g., LEAP.ActiveScenario

Please use the [Script
Editor](Using_the_Script_Editor.md) for documentation of the properties and methods of the Scenarios
API. The right-hand pane of the Script editor fully enumerates all collections
and objects in the LEAP API.