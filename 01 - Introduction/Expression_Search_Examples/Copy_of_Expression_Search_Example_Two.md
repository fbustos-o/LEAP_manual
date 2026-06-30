---
Source: https://leap.sei.org/help24/Concepts/Expression_Search_Examples/Copy_of_Expression_Search_Example_Two.htm
---

# Expression Search Example 2:  scenario hierarchy with multiple inheritance

See also: [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md), [Example One](Expression_SearchExample_One.md), [Example Three](Expression_Search_Example_Three.md), [Example Four](Expression_Search_Example_Four.md)

Now, building on [example 1](Expression_SearchExample_One.md), suppose that your mitigation scenario is actually a package of 3 other scenarios: GHG mitigation measures that could be conducted individually in the industry, buildings and transport sectors. This package of scenarios is constructed by specifying additional scenarios upon which the mitigation scenario is based in the First Inherits From box of the [Manage Scenarios](../../16%20-%20Supporting%20Screens/Scenario_Manager.md) screen. You can see how such this set of scenario would look in the Manage Scenarios screen in Figure 2a.

![](../../assets/images/NewScreens/Scenarios%20EX2.png)

Figure 2b: A scenario hierarchy with multiple inheritance in LEAP's Scenario Manager

For these scenarios, the following expression search process is followed (shown in Figure 2a).  LEAP first looks in the active scenario, which in this case is Mitigation (STEP 1). If no expression is found, LEAP looks in each of the three additional scenarios (industry, buildings and transport) in the order shown on the Manage Scenarios screen (STEP 2). LEAP then proceeds to walk up the main scenario tree, first to the Baseline scenario and then to Current Accounts (STEP 4). Ultimately, if no expression is found then the default value for the variable is used.

The full expression search order is as follows: Mitigation, Industry, Buildings, Transport, Baseline, Current Accounts, Default Value.

![](../../assets/images/Logos/ExpSearchEx2.png)

Figure 2b: Search Process for a Variable in the Mitigation Scenario: Package of Scenarios

Search Key (for more detail, see [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md)):

* Step 1: Current active scenario
* Step 2: Additional scenarios listed in the First Inherits From box
* Step 3: Additional scenarios affecting those listed in Step 2.  (not applicable in this example)
* Step 4: Finally walk backup main scenario tree.