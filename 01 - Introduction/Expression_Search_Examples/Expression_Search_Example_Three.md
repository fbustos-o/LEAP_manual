---
Source: https://leap.sei.org/help24/Concepts/Expression_Search_Examples/Expression_Search_Example_Three.htm
---

# Expression Search Example 3:  A scenario hierarchy with a "Package of packages"

See also: [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md), [Example One](Expression_SearchExample_One.md), [Example Two](Copy_of_Expression_Search_Example_Two.md), [Example Four](Expression_Search_Example_Four.md)

Now, building on [example two](Copy_of_Expression_Search_Example_Two.md),  let's imagine that your transportation scenario is itself based on a package of 3 additional scenarios: mitigation measures for cars, buses and rail. In other words, the transport package is itself a package of packages  You can see how this scenario structure would be entered in LEAP's Scenario Manager in Figure 3a.  Notice in the Scenario tree that the Mitigation scenario inherits from the Transport, Buildings and Industry scenarios, and that the Transport scenario inherits from the cars, buses and rail scenarios.

![](../../assets/images/NewScreens/Scenarios%20EX3A.png)

Figure 3a: A Scenario Hierarchy with a Package of  Packages in LEAP's Scenario Manager

In this situation the expression search process is as follows.  First, LEAP looks in the active scenario, in this case Mitigation (STEP 1). Next LEAP looks in each of the additional scenarios  (industry, buildings and transport), which are listed in the First Inherits From box of [Manage Scenarios](../../16%20-%20Supporting%20Screens/Scenario_Manager.md) screen (just as described in example 2).  This is STEP 2  Next, LEAP looks through each of these additional scenarios to see if they themselves are based on other scenarios (i.e. whether they have scenarios listed in their First Inherits From box).  In this example, the Transport scenario is itself a package of three scenarios describing mitigation measures for cars, buses and rail (STEP 3).   If no non blank expression is found, LEAP then walks up the main scenario tree, first to the Baseline scenario expression and then to Current Accounts (STEP 4). Ultimately, if no expression is found then the default value for the variable is used.

The full expression search order is as follows: Mitigation, Industry, Buildings, Transport, Cars, Buses, Rail, Baseline, Current Accounts, Default Value.

![](../../assets/images/Logos/ExpSearchEx3.png)

Figure 3b: Search Process for a Variable in the Mitigation Scenario: Package of Packages

Search Key (for more detail, see [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md)):

* Step 1: Current active scenario
* Step 2: Additional scenarios listed in the First Inherits From box
* Step 3: Additional scenarios affecting those listed in Step 2.
* Step 4: Finally walk backup main scenario tree.