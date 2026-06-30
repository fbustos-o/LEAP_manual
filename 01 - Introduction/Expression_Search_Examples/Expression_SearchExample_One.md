---
Source: https://leap.sei.org/help24/Concepts/Expression_Search_Examples/Expression_SearchExample_One.htm
---

# Expression Search Example 1:  A Simple Scenario Hierarchy

See also: [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md), [Example Two](Copy_of_Expression_Search_Example_Two.md), [Example Three](Expression_Search_Example_Three.md), [Example Four](Expression_Search_Example_Four.md)

Let's examine a simple example with just one baseline scenario and one mitigation scenario.  You can see how such a scenario hierarchy looks in this screen capture of LEAP's Scenario Manager (Figure 1a)

![](../../assets/images/NewScreens/Scenarios%20EX1.png)

Figure 1a: A Simple Scenario Hierarchy in LEAP's Scenario Manager

Now suppose LEAP needs to find the expressions for a given branch and variable (e.g. Demand/Industry:Activity Level) in the Mitigation Scenario.  The following is the process used for Searching for an expression:

First LEAP looks in the active scenario, in this case Mitigation (Step 1 above) . If no expression is found, LEAP walks up the main scenario tree (STEP 4 above) first to the Baseline scenario and ultimately to the Current Accounts data until a non-blank expression is found.  Ultimately, if no expression is found then the default value for the variable is used.  This expression search process is illustrated graphically in Figure 1,

This example is a typical situation in may data sets in which you enter any historical or static data in the Current Accounts and then enter a complete description of how your energy system is likely to change over time under current policy conditions in the Baseline scenario.  The data in the mitigation scenario only needs to specify how the mitigation scenario is likely to be different from the data already specified in the Baseline or Current accounts

The full expression search order is as follows: Mitigation, Baseline, Current Accounts, Default Value.

![](../../assets/images/Logos/ExpSearchEx1.png)

Figure 1b: : Search Process for a Variable in the Mitigation Scenario: Simple Hierarchy

Search Key (for more detail, see [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md)):

* Step 1: Current active scenario
* Step 2: Additional scenarios listed in the First Inherits From box  (not applicable in this example)
* Step 3: Additional scenarios affecting those listed in Step 2.  (not applicable in this example)
* Step 4: Finally walk backup main scenario tree.