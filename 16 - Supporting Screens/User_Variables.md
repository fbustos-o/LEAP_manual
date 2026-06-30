---
Source: https://leap.sei.org/help24/Supporting_Screens/User_Variables.htm
---

# User Variables

Menu Option: Analysis: User Variables  
See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Key Assumptions](../21.6%20-%20Wizards%20and%20Properties/Macrovariable_Properties_Wizard.md), [Indicators](../14%20-%20Indicators/Indicators.md), [Variable Categories](Variable_Categories.md), [Tags](../15%20-%20Tagging%20Branches/Manage_Tags.md)

## Introduction

In addition to the many variables defined by LEAP, you can also create up to 400 of your own User Variables.  A User Variable will be added as a tab in the data entry screens of the [Analysis View](../02%20-%20Views/Data_View.md).  You can specify data for user variables in Current Accounts and scenarios.  User Variables are currently available for use in your own intermediate calculations of the [Analysis View](../02%20-%20Views/Data_View.md). They cannot currently be reported in the Result Views. However, you may refer to these variables just as you would any other variables in the Analysis View, and the values of user variables can be specified using all of the same expressions available to other LEAP variables.

## Editing User Variables

You can use the Analysis: User Variables screen to view and edit all User Variables.  Alternatively, you can right-click on one of the User Variable tabs in the Analysis View to Add (![](../assets/images/NewButtons/Add.png)), Delete (![](../assets/images/NewButtons/Delete.png)), and edit (![](../assets/images/NewButtons/rename.png)) a User Variable or to make a new variable as a Duplicate copy of an existing one.

Each user-defined variable has the following information associated with it:

## Basic Information

* Name: The label that appears on the Analysis View tab associated with the variable.
* Scale/Units:  The scaling factor and units in which the variable is measured.  Note that these data are for information only.  The unit is entered as text.
* Category: Use this box to assign a variable to a particular category.  LEAP has a number of default categories (basic variables, cost variables, environmental variables, etc.).  You can also add your own variable categories using the Analysis: Variables: [Variable Categories](Variable_Categories.md) screen.  This screen is also accessible from the toolbar in the User Variables screen.
* Notes: a longer description of the variable, that will be displayed in a panel whenever the variable is being edited.
* Time-Sliced Variable: Use this check box to indicate if a user variable is to be specified with sub annual data (e.g. seasonal or time-of-day values). Use the [General: Time Slices](Time_Slices.md) screen to view or edit the time slices into which each year is divided.
* Intermediate Variable: You can optionally mark a user variable as an Intermediate variable (i.e. one that has been created primarily to contain intermediate calculations but would be of lesser interest to non-modelers).  In the Analysis View screen you can right-click on the variable tabs and choose to display  All User Variables,  No Intermediate Variables or None (No User Variables).

## Defaults

* Default Expressions:  You can set default expressions for user variables for both Current Accounts and scenarios.  Default expressions can be simple values or they can be complex expressions that utilize the functions and variable references. If the scenario default expression is left blank, the default will be the same as for Current Accounts (based on LEAP's standard [expression inheritance](../01%20-%20Introduction/Understanding_Expression_Inheritance.md)).
* Read-Only: Use this check box to indicate if a user variable is editable by the user in the Analysis View. You may want to set variables that are always calculated using the same default expression as read only.

## Visibility

* Scenario Visibility: Use the Current Accounts and Scenario check boxes to set whether a user variable is visible in Current Accounts and scenarios.  If unchecked, the variable (tab) will not appear in the Analysis view.  You can uncheck both boxes to temporarily hide a user variable. Note that hiding a user variable does not delete any of its data.
* Tag Visibility: You can add [tags](../15%20-%20Tagging%20Branches/Manage_Tags.md) to limit the visibility of user variables to only those branches containing one or more of the listed tags.  If blank, the user variable will be visible at any branch (whether it is tagged or not).    
    
  Tags should be typed in separated by commas, or you can add an existing tag by pressing the ![](../assets/images/NewButtons/tag.png) Tag button and selecting the ![](../assets/images/NewButtons/Add.png) Add button, or delete a tag using the ![](../assets/images/NewButtons/Delete.png) Delete button. You can organize your tags into color coded groups using the Manage Tags option (![](../assets/images/NewButtons/tag.png)), which can also be accessed from the [Tags](../15%20-%20Tagging%20Branches/Manage_Tags.md) menu  on the main screen (Alt+T).
* Branch Visibility:  You can set the types of tree branches at which each user variable is available: All branches or Demand branches (all, technologies or categories), Transformation branches (all, modules, processes or outputs), Environment, Resources, Statistical Differences, Stock Changes, Non-energy sector effects, and Indicators.
* Available On & Below Branch: You can also select the tree branches where the user variable will appear.  So for example, you might choose to show a user variable at all technology branches on and below the Transport sector branch.  Use the check boxes to select if a variable is visible on and/or below the selected branch.  You can also specify if a variable is only visible at a certain specified number of levels below the named branch.  For example some user variables may be visible one level below the named branch, while others might be visible at all levels below the named branch.

## Min/Max

* Min/Max Values:  You can set minimum and maximum allowable values for user variables.  LEAP's data will later be tested to ensure these values remain within the specified minimum and maximum constraints.  Leave fields blank if you do not want to specify minimum or maximum values.

Note: In addition to defining your own User Variables you can also create variables under the [Key Assumptions](../21.6%20-%20Wizards%20and%20Properties/Macrovariable_Properties_Wizard.md) and [Indicators](../14%20-%20Indicators/Indicators.md) categories on the tree.

## When to use Key Assumptions and when to use User Variables?

There is no single best practice for when to enter data under Key Assumptions or when to enter it within [User Variables](User_Variables.md). It is up to the user to decide what works best for them. However, there are a few points to consider when making this choice:

* Try to create the least complicated and most easily understood model that meets your needs. Sometimes user variables are best because they can house data close to where it is needed in your Demand Analysis.  For example, data on air conditioner usage could be placed in a user variable under the Household\Air Conditioning branch in your energy demand analysis. With this approach, the equations you write that reference the user variables won't need to include long path names (e.g. "key Assumptions\Household\Air Conditioning\...").
* On the other hand, if you ever need to point to a variable from many different places or sectors then Key Assumptions may be more efficient, since you will be entering data in a single place.  The more you can reduce the complexity of the tree structure the faster your model will calculate and the easier it will be to interpret and maintain your model at a later date.  Remember also that the users of a model may not be the same people who originally built it. Simplicity (as far as possible), clarity and transparency are vital for making your model useful to others (see also model documenation using the [Notes View](../03%20-%20Interface/Notes.md)).
* Another clear advantage of storhing data in User Variables is that the data will appear (as tabs) close to where it is used: thus making the modeling easier to understand and reducing the need for users to do a lot of navigation (clicking) within the tree.