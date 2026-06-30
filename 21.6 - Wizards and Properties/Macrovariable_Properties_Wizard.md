---
Source: https://leap.sei.org/help24/Wizards_and_Properties/Macrovariable_Properties_Wizard.htm
---

# Key Assumptions

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [User Variables](../16%20-%20Supporting%20Screens/User_Variables.md) , [Indicators](../14%20-%20Indicators/Indicators.md)

![](../assets/images/NewScreens/KeyAssumptionProperties.png)

## Introduction

In the [Analysis View](../02%20-%20Views/Data_View.md), the first major category on the tree is labeled Key Assumptions. Key Assumptions are general purpose variables that you can create and later refer to in the other parts of your model including in the Demand, Transformation and, and Non-energy sector branches.   Most commonly under Key Assumption branches, users will create variables representing macroeconomic, demographic and other variables. It can also be used to represent data that you want to reuse and refer to in multiple other branches of the tree

## Using the Key Assumptions Screen

Use the Key Assumption's Properties screen (![](../assets/images/NewButtons/Properties.png)) to create and then edit the name and units of each Key Assumption.  Key Assumption branches can be of two types:

![](../assets/images/NewButtons/folder.png) Category Branches, which are used for organizing key assumptions into a hierarchical data structures. These branches do not contain data.

![](../assets/images/NewButtons/key.png) Key Assumption Branches, which are used to indicate variables and data (e.g. GDP, industrial output, population, consumption, investment etc). These variables are not output as results from LEAP, but are used instead as intermediate variables that can be referenced in your Demand, Transformation and Resource models. When adding key assumptions, enter the unit of the variable as text.

Note: in addition to defining variables under the Key Assumptions category, you can also add your own [User Variables](../16%20-%20Supporting%20Screens/User_Variables.md) within your Demand, Transformation and Resource analyses. Use the General: [User Variables](../16%20-%20Supporting%20Screens/User_Variables.md) screen to define your own User Variables. You can also create [Indicator](../14%20-%20Indicators/Indicators.md) variables for reporting additional calculated results.

## When to use Key Assumptions and when to use User Variables?

There is no single best practice for when to enter data under Key Assumptions or when to enter it within [User Variables](../16%20-%20Supporting%20Screens/User_Variables.md). It is up to the user to decide what works best for them. However, there are a few points to consider when making this choice:

* Try to create the least complicated and most easily understood model that meets your needs. Sometimes user variables are best because they can house data close to where it is needed in your Demand Analysis.  For example, data on air conditioner usage could be placed in a user variable under the Household\Air Conditioning branch in your energy demand analysis. With this approach, the equations you write that reference the user variables won't need to include long path names (e.g. "key Assumptions\Household\Air Conditioning\...").
* On the other hand, if you ever need to point to a variable from many different places or sectors then Key Assumptions may be more efficient, since you will be entering data in a single place.  The more you can reduce the complexity of the tree structure the faster your model will calculate and the easier it will be to interpret and maintain your model at a later date.  Remember also that the users of a model may not be the same people who originally built it. Simplicity (as far as possible), clarity and transparency are vital for making your model useful to others (see also model documenation using the [Notes View](../03%20-%20Interface/Notes.md)).
* Another clear advantage of storhing data in User Variables is that the data will appear (as tabs) close to where it is used: thus making the modeling easier to understand and reducing the need for users to do a lot of navigation (clicking) within the tree.

##