---
Source: https://leap.sei.org/help24/Concepts/Understanding_Expression_Inheritance.htm
---

# Understanding Expression Inheritance

See also: [Scenarios](Scenarios.md), [Manage Scenarios](../16%20-%20Supporting%20Screens/Scenario_Manager.md), [Expressions](Expressions.md)

Nearly all data in LEAP are specified as [expressions](Expressions.md) for a given variable at a given branch in the LEAP [Tree](../03%20-%20Interface/TreeOverview.md).  These expressions are entered in LEAP's [Analysis View](../02%20-%20Views/Data_View.md) (**![](../assets/images/NewButtons/Views/Analysis.png)**) and different expressions can be entered for different scenarios (or for different regions in a [multi-region](../16%20-%20Supporting%20Screens/Regions.md) area).  To minimize data entry requirements, scenarios are organized in a hierarchy so that you need only enter data in one scenario if it differs from the data entered in its parent (ancestor) scenario.

Understanding the way that expression inheritance works in LEAP is fundamental to understanding how scenarios help you manage data.

## Expression Search Order

Whenever LEAP calculates a value for a particular variable at a particular branch, scenario and region, the value of that variable is based on evaluating the expression defined for that branch, variable, scenario and region.  LEAP uses a specified search order to look for these expressions.  At each step in the search, LEAP looks to see if a non-blank expression has been explicitly entered.  If a non blank expression is found the search concludes successfully, and the expression is used to calculate a set of values for the currently active branch, variable, scenario and region.  If no non-blank expression is found the search continues.  The search works as follows:

1. Step 1: First LEAP looks in the current active scenario to see if an expression has been explicitly entered.

   Step 2: Next, it looks in order through each of the additional scenarios listed in the First Inherits From box of the [Scenarios](../16%20-%20Supporting%20Screens/Scenario_Manager.md) screen (**![](../assets/images/NewButtons/Scenarios.png)**). This allows scenarios to be made up of packages of other scenarios.  For example, a mitigation scenario might consist of measures in the transport, industry and buildings sectors.

   Step 3: Next for each of these additional scenarios LEAP looks through any additional scenarios that these scenarios depend on.  This allows you to create "packages of packages" of scenarios.  For example a transport scenario might itself consist of measures addressing cars, buses, rail, etc.

   Step 4: Next if an expression still has not been found, LEAP walks up the main scenario tree from the currently active scenario back to the Current Accounts data.

Multiple Region Areas: When working in areas with multiple regions, the same basic search order described above is used.  The only exception is that if a region is set to inherit expressions from another parent region then, at each step in the expression search process, LEAP will first look in the current active region, and then, if no expression is found, it will look in the parent region for the scenario currently being searched.

Ultimately,  if no non-blank expression is found in any searched scenario or region then a default expression for the variable is used to calculate the values (typically a zero for most variables).

## Examples of Expression Search

The expression search process can perhaps best be understood by considering a number of examples.  Four examples of scenario inheritance are considered:

[Example 1. A Simple Scenario Hierarchy](Expression_Search_Examples/Expression_SearchExample_One.md)

[Example 2. A Scenario Hierarchy with Multiple Inheritance (a Package of Scenarios)](Expression_Search_Examples/Copy_of_Expression_Search_Example_Two.md)

[Example 3. A Scenario Hierarchy with a Package of Packages of Scenarios.](Expression_Search_Examples/Expression_Search_Example_Three.md)

[Example 4. A Scenario Hierarchy with Multiple Regions.](Expression_Search_Examples/Expression_Search_Example_Four.md)