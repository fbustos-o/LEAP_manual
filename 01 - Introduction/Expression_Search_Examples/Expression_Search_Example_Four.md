---
Source: https://leap.sei.org/help24/Concepts/Expression_Search_Examples/Expression_Search_Example_Four.htm
---

# Expression Search Example 4:  A scenario Hierarchy with Multiple Regions

See also: [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md), [Example One](Expression_SearchExample_One.md) [Example Two](Copy_of_Expression_Search_Example_Two.md), [Example Three](Expression_Search_Example_Three.md)

Now let’s go back to the simple scenario structure used in [Example One](Expression_SearchExample_One.md) with only one Baseline and one Mitigation Scenario.  But now let’s imagine that we have two regions: Region A and Region B. In this case assume that Region B has been set to inherit its expressions from Region A.  This can be done on the General: [Regions](../../16%20-%20Supporting%20Screens/Regions.md) screen. Now let's look at the search process for a branch and variable in Region B in the mitigation scenario.

LEAP first looks in the active scenario - in this case Mitigation (STEP 1). If no non blank expression is found, LEAP proceeds to look in Region A for that same scenario (STEP 1a). . If no non blank expression is found, LEAP proceeds to walk up the main scenario tree towards Current Accounts. For each scenario it first looks in the current active region (Region B) and then in Region A.  These are STEPS 4 and 4A respectively.  Ultimately, if no expression is found then the default value for the variable is again used.

The full expression search order is as follows: Mitigation (B), Mitigation (A), Baseline (B), Baseline (A), Current Accounts (B), Current Accounts (A), Default Value.

![](../../assets/images/Logos/ExpSearchEx4.png)

Figure 4: : Search Process for a Variable in Region B in the Mitigation Scenario: Simple Scenario Hierarchy /Multiple Regions

Search Key (for more detail, see [Understanding Expression Inheritance](../Understanding_Expression_Inheritance.md)):

* Step 1/1a: Current active scenario
* Step 2: Additional scenarios listed in the First Inherits From box (not applicable in this example)
* Step 3: Additional scenarios affecting those listed in Step 2.  (not applicable in this example)
* Step 4/4a: Finally walk backup main scenario tree.