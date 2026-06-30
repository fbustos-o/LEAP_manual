---
Source: https://leap.sei.org/help24/Expressions/Results_Filters.htm
---

# Referencing Results in Expressions

See also: [Expressions](../01%20-%20Introduction/Expressions.md), [Referencing Data in Expressions](Referencing_Other_Data_Variables_in_Expressions.md)

## Summary

You can reference both data variables and results variables. Data variables are those that are specified directly in LEAP's Analysis View through LEAP's expressions. Results variables are the additional values calculated internally by LEAP.  Results variables include values such as total final energy demand, total emissions or total costs, as well as many other types of results.

You can create references to results variables by dragging and dropping items from the Analysis View tree into the Expression Builder, by using LEAP's built-in code completion features, or by using the [Branch/Variable Wizard](../16%20-%20Supporting%20Screens/Branch_Variable_Picker.md) (Ctrl+B).

## Syntax

The standard syntax for referencing results variables is as follows:

Branch:Variable[Scale Unit, FilterDim1=FilterElement, FilterDim2=FilterElement2]

Filters can be specified either as dimension=element (to get results for the listed element), or dimension<>element (to get the results for all elements except the named element).

For example:

Freedonia:Global warming potential C eq[Million kg, Fuel=Gasoline]

If the contents of the square bracket are omitted, LEAP will automatically add the default scaling factor and units in which the referenced variable is measured.  later you can changed these scaling factors and units to match the required scale and units for the variable you are calculating.  For example, if the default units returned is kilogramme (kg) but you require the result in Short Tons, you can simply edit the text in the box and LEAP will return the result in the new unit.

If the filtering text is omitted, LEAP will return the total value of the result at the specified branch.  Use the optional filtering text to show the demand for a particular element, such as the emissions from combustion of a particular fuel.  You can specify up to two filters on a result. Allowable dimensions are: fuel, cost, time slice, effect, balance category, module cost category or tag.  The allowable elements depend on the dimension.  For example, for the fuels dimension the allowable elements are the [fuel names](../16%20-%20Supporting%20Screens/Fuels.md) defined for your analysis,  Similarly for effects, the allowable elements are the [effect names](../16%20-%20Supporting%20Screens/Effects_Screen.md) defined for your analysis.

Because they are calculated internally, in general, you can only reference results that were calculated in a previous year. This is done by using the [PrevYearValue](PrevYearValue.md) or [LaggedValue](LaggedValue.md) functions to reference a past value of a result variable.

For example you might write:

PrevYearValue(Freedonia:Global warming potential C eq[Million kg, Fuel=Gasoline])

An exception is when specifying calculated [Indicator](../14%20-%20Indicators/Indicators.md) variables.  Because these are calculated after LEAP's main calculation routines they may include references to the present-year value of results variables.