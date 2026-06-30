---
Source: https://leap.sei.org/help24/Expressions/Referencing_Other_Data_Variables_in_Expressions.htm
---

# Referencing Data and Constants in Expressions

See also: [Expressions](../01%20-%20Introduction/Expressions.md), [Referencing Results in Expressions](Results_Filters.md)

## Introduction

In addition to using expressions to directly specify data, you can also create expressions that refer to the values of other variables in LEAP.  In this way you can create your own models that include both exogenous (externally specified) data and endogenous (internally calculated) variables. You can reference both data variables and results variables.  Data variables are those that are specified directly in LEAP's Analysis View through LEAP's expressions. Results variables are the additional values calculated internally by LEAP.  Results variables include values such as total final energy demand, total emissions or total costs, as well as many other types of results.

You can create references to data variables by dragging and dropping items from the Analysis View tree into the Expression Builder, by using LEAP's built-in code completion features, or by using the [Branch/Variable Wizard](../16%20-%20Supporting%20Screens/Branch_Variable_Picker.md) (Ctrl+B).

## Naming Syntax

The general syntax of branch/variable references is:

Path\Branch:Variable[Scale Unit]

Data values are referenced by specifying the branch path followed by a colon followed by the variable name. For example, the value of the activity level variable in the Demand\Households branch would be referenced by typing Demand\Households:Activity Level. Expressions are not case-sensitive. You can enter variable and function names in any combination of upper and lower-case letters. When you submit the formula, LEAP will put the names into a standard format:capitalizing the names of variables and following the branch name capitalizations shown in the tree. When referencing branches that are immediate siblings or parents of the current branch, you need only specify the last part of the branch name (e.g. Cooking). When referencing more distant branches, include the full path name (e.g. Demand\Households\Urban\Cooking).  When referencing another variable at the same branch, you need only enter the variable name. Similarly, when referencing the same variable but at a different branch you need only enter the branch name.    
  
Normally, you will create references to a variable at a branch where that variable occurs.  However, LEAP also allows you to create references to a variable at higher level branches.  LEAP will then return the sum of the values for all descendant branches where that variable occurs.  For example you may have specified data on separately on the size of urban and rural populations under a Key Assumption category called "Population".  You could then calculate the total population (urban + rural) through the following reference: Key\Population[people] even though the Population category branch itself has no key assumption variable.

## Specifying Scaling Factors and Units

When you referencing a variable, LEAP will automatically append the scale and units of the referenced variable in square brackets written immediately following the variable name.  For example, if you enter a branch/variable reference to an Activity Level variable with a scale and units of Million Person as:

Households: Activity Level

LEAP will change this to read

Households: Activity Level[Million Person]

Some variables have no associated scaling factors and thus the square bracket will simply contain the unit name.  You can subsequently edit the scale and units specified within the square brackets and LEAP will convert the values returned to the scale and units you specify.  Note however, that you must specify a unit of the same class as the one specified for the referenced variable,   For example, if the referenced variable is measured in a mass unit (e.g. "Tonne"), you may specify another mass unit (e.g. "kg")  but using a volume unit such as liters, or any a unit of any other class will generate an error message.  You can specify units either using their long names (e.g. kilogram) or using their abbreviations (kg).  Refer to the [General: Units](../16%20-%20Supporting%20Screens/Units.md) screen for a full list of available units.  The allowable scaling factors values are:  % (10E-2), Hundred (10E2), Thousand (10E3), Million (10E6), Billion (10E9) and Trillion (10E12). Users in India may also use Lakh (10E5) and Crore (10E7).  Note that you can reset an expression to use the default scaling factors (those used in the referenced variable) by simply deleting the contents of the square brackets.

## Filtering References to Data Variables

As with results variables, you can specify a filter on a reference to a data variable to limit the branches summed.  For data variables, the only type of filter that can be applied is the Tag filter. In addition, only "Tag=" is supported (not "Tag<>").

As an example, imagine that you want to calculate the number of households using clean cooking fuels (e.g. electricity, natural gas or LPG) based on a disaggregated data structure similar to the one used in the sample Freedonia data set shown on the right (with clean cook stoves marked in red).

To accomplish this, add the same tag word (e.g. "clean") to each clean cooking technology.  The number of households using those technologies can then be calculated (e.g. in an indicator branch) by referencing the Total Activity variable as follows:

Demand\Household:Total Activity[Household, Tag=clean]

## Fuel Variables

A further type of variable you can reference in expressions is fuel variables. These are the various chemical and physical characteristics of the fuel associated with a branch. Examples include the carbon, sulfur, and moisture content of the fuel, and its net heating value. Notice that only branches in which fuels are consumed or produced have valid fuel variables. These fuel variables reflect the data defined in the [Fuels](../16%20-%20Supporting%20Screens/Fuels.md) screen.

## Constants

Constants, including your own user-defined constants, can also be included in expressions. A default set of constants are included that define various molecular weight constants. These are primarily useful in defining emission factors. For example, a CO2 emission factor might be a function of the carbon content of the fuel, the fraction of the fuel oxidized, and the molecular weights of carbon and carbon dioxide.

## TED Variables

[TED](../21.3%20-%20TED/TED_Intro.md) Branches and variables can also be referenced in expressions. The syntax is similar to that used for referencing LEAP variables (i.e. branch:variable), except that a special function TED() needs to be wrapped around the reference. Referencing TED data allows you to selectively use items of data stored in the TED database in your calculations.