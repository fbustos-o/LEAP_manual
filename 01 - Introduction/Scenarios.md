---
Source: https://leap.sei.org/help24/Concepts/Scenarios.htm
---

# Scenarios

See also: [Manage Scenario](../16%20-%20Supporting%20Screens/Scenario_Manager.md)s, [Understanding Expression Inheritance](Understanding_Expression_Inheritance.md)

## Overview

At the heart of LEAP is the concept of scenario analysis. Scenarios are self-consistent story-lines of how a future energy system might evolve over time in a particular socioeconomic setting and under a particular set of policy conditions. Using LEAP, scenarios can be built and then compared to assess their energy requirements, social costs and benefits and environmental impacts.  You can use scenarios to ask an unlimited number of "what if" questions, such as: what if more efficient appliances are introduced, what if different electric generation capacity expansion plans are pursued, what if indigenous reserves of oil and gas are discovered, what if renewable energy technologies are introduced, etc.

All scenarios share a common set of Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year. data.  Current Accounts data may either reflect a single set of base year data or may represent multiple years of historical data.  Each scenario runs from the First Scenario Year to the End Year of the study.  In cases where the Current Accounts is for only a single year, then the First Scenario Year will be the year immediately after the base year.

Scenarios in LEAP encompass any factor that can change over time, including those factors which may change because of particular policy interventions, and those that reflect different socioeconomic assumptions. Variations, in these latter types of factors are normally referred to as a sensitivityChanges that occur in a scenario because of different socio-economic assumptions, rather than because of different policies. . In LEAP, sensitivities are included in a scenario. Because of this, it is important in your cost-benefit analysis that you only compare scenarios with the same socioeconomic assumption.

## Understanding Expression Inheritance

Nearly all data in LEAP are specified as expressions for a given variable at a given branch in the LEAP tree. These expressions are entered in LEAP's [Analysis View](../02%20-%20Views/Data_View.md) and different expressions can be entered for different scenarios (or for different regions in a multi-region area).  To minimize data entry requirements and to make data management as easy as possible, scenarios are organized in a hierarchy so that you need only enter data in one scenario if it differs from the data entered in its parent (ancestor) scenario.    Before describing the scenario manager, it is important to first understand the way that expression inheritance works in LEAP since this is fundamental to understanding how scenarios help you manage data.  See [Understanding Expression Inheritance](Understanding_Expression_Inheritance.md) for more information.