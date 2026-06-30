---
Source: https://leap.sei.org/help24/Supporting_Screens/Fuels.htm
---

# Fuels

Menu Option: General: Fuels (also shown on the [main toolbar](../03%20-%20Interface/Main_Toolbar.md))  
See Also: [Fuel Groupings](Balance_Catagories.md), [Fuel Grouping Names](Fuel_Grouping_Names.md), [Settings](Basic_Parameters_Screen.md)

![](../assets/images/NewScreens/Fuels.png)

## Introduction

The fuels screen is the place where you can view or edit the list of fuels used in your LEAP analysis. The screen displays a wide range of data about the energy content, density, carbon content, and chemical composition of each fuelSomething combusted, or otherwise used to produce energy and also includes detailed definitional notes and references for the included data (in the bottom two panes of the screen).

The default data provided with LEAP includes a standard fuels database based on IEA, UN and other standard international sources of data. This data should suffice for most LEAP analyses. However, you may wish to edit the data, for example to change the energy contents of certain fuels (especially coal and wood) to reflect the conditions in the Area you are studying. You may also wish to change the names of fuels to reflect the language in which your analysis will be conducted, or edit up to four sets of named fuel groupings which can be used in the [Results](../02%20-%20Views/Results_Screen.md) and [Energy Balance](../02%20-%20Views/Energy_Balance_View.md) views for viewing results summed across these fuel groupings.

## Using the Fuels Screen

Use the **Add** (![](../assets/images/NewButtons/Add.png)) button to add a new fuel and the **Delete** button (**![](../assets/images/NewButtons/Delete.png)**) to delete a fuel. Note however, that you cannot delete any fuels already in use in your analysis or in use in the TED database. It is recommended that you do not delete fuels in the Fuels database. Click the **![](../assets/images/NewButtons/MS-Excel.png)** button to export the fuels database to Microsoft Excel.  Click the ditto button (**![](../assets/images/NewButtons/Ditto.png)**) to duplicate a field value from the value immediately above it.

Some of the data fields in the fuels screen are worth describing in more detail:

* Order: Use the Up (![](../assets/images/NewButtons/Arrow-up.png)) and Down (![](../assets/images/NewButtons/Arrow-down.png)) buttons to move a fuel up or down in the ordered list of fuels.  Note that you can also sort fuels by name, state, type, and fuel grouping by clicking the appropriate column title.  The ordering buttons only work when you sort by order by clicking the Ord column title.
* Name: You can edit each fuel name (for example to reflect local language settings).  Note that you may not create duplicate fuel names.  Also, some names are reserved in LEAP (for example function names.  LEAP will not allow you to name a fuel with a reserved name.
* State: the chemical state of the fuel (solid, liquid, gas or energy). This field can only be edited when adding a new fuel.
* Type: Each fuel is classified into one of five types: fossil resource, renewable resource, biomass resource, secondary fuelA fuel produced by conversion from a primary fuel., and electricity (a special type of secondary fuel). LEAP uses these classifications to determine how each fuel should be handled in your analysis.
* Grouping : When producing energy balances and other reports, it is sometimes useful to be able to show results aggregated across certain types of fuels (for example, showing all oil products rather than each individual product). To allow for this, LEAP allows you to assign a fuel groupings to each fuel. You can change the chosen fuel grouping by editing the data in the Fuels screen.  Use the General: [Fuel Groupings](Balance_Catagories.md) screen to create up four different named sets of Fuel Groupings.
* Resource By Land-Type:  This yes/no switch indicates if resources will be specified disaggregated by land-type.  This is useful when specifying more detailed assessments of biomass and renewable energy resources where you wish to specify resources per unit of land area for each land-type.  Using this approach requires that you also enable the Setting Land-Use Change and Land-Based resources on the Scope & Scale tab of the [Settings](Basic_Parameters_Screen.md#Scope) screen.
* Trade Among Regions: Use this option to specify which if any resources may be trade among regions.  It is only relevant for multi-region areas and is used in conjunction with the [In-Area Import Fraction](../10%20-%20Resources/In-Area_Import_Fraction.md) and [In-Area Export Fraction](../10%20-%20Resources/In-Area_Export_Fraction.md) variables shown under the Resources branches.
* **Has Load Shape:** Use this column to choose which fuels will have load shapes associated with them.  Selecting fuels in this column will cause those fuels to appear in the main Tree listed under the high level Load Shapes branch.
* Net Energy Content: Energy contents are always net (lower heating values) in LEAP. The default energy contents are typical values and conform to official IEA figures wherever possible. Energy content values are entered in a chosen energy unit per physical unit of the fuel. Pure energy forms (electricity and heat) should always have an energy content of 1 GJ/GJ by definition. When entering energy contents for coal (which varies widely from country to country), refer to the notes for each fuel for guidance on average values for selected countries.
* Chemical Composition Columns (Density, %Carbon, %Sulfur, %Nitrogen, etc.): Environmental emissions associated with energy production and consumption often depend on the physical and chemical composition of the fuel involved. In TEDThe Technology and Environmental Database., you can optionally choose to enter emissions coefficients dependent on fuel compositions. This can be useful, for example, when you are entering data describing CO2 emissions from coal fired electricity generating plants. For this type of data the actual emissions will not simply depend on the quantity of coal consumed by the plant, but will also depend on the carbon content of the coal. By editing the fuel compositions shown here to more accurately reflect the compositions of the fuels used in the areaThe energy system being studied you are studying, you can more accurately calculate the total emissions loadings of your scenarios, often without the need to create new entries in TED).
* Carbon Stored When Fuel Consumed for Non Energy Purposes (%): Indicates the fraction of the carbon in the fuel (by weight) that remains permanently stored when the fuel is used for non-energy purposes.  This variable is used in conjunction with the non-energy fraction variable in an energy demand analysis.

By default, the fuels screen is filtered to display only those fuels currently being used in your area. To see the full list of fuels, choose Show: All Fuels. Use the Find box to quickly locate a fuel by name.

You can also sort the display of fuels by name, state, type and category by clicking on the appropriate column title.  A sort indicator is displayed in the column title to show which column is used to sort the table. The indicator shows the sort order using a triangle pointing up for ascending or down for descending sorts.