---
Source: https://leap.sei.org/help24/Screen_Layout/Types_of_Tree_Branches.htm
---

# Tree Branches

Different types of branches in the tree are represented as different icons or pictures. The types of data entered at each branchAn item on the tree. Different types of branches are represented by different icons on the tree (i.e. the tabs that appear in Analysis View), will depend on the type of branch, its position in the tree (for example whether it is a Demand or Transformation branch), and the properties you set for that branch. The meaning of each icon is explained below:

![](../assets/images/NewButtons/Tree/Key.png)Key Assumption branches are used to indicate independent time-series variables. (e.g. GDP, industrial output, population, consumption, investment etc.) Key Assumptions are not directly calculated in LEAP, but can be useful as intermediate variables that can be referenced in your modeling calculations. Key Assumptions are defined globally and then used in the different analyses as a means of projecting results. For example, they can be used in the Demand program in conjunction with elasticities to project energy demands.

![](../assets/images/NewButtons/Tree/folder.png) **CategoryA type of branch used primarily to organize other branches into a hierarchical structure in the LEAP and TED trees. branches** are the most common type of branch. They are used mainly for organizing the other branches into hierarchical data structures. For example, in your demand analysis, you can use category branches to create a set of sectors, subsectors and end-uses, into which you place the various energy-using devices you wish you model. In Demand branches these data structures are very flexible. You can create any number of levels of branches, and use different levels in different sectors. In your Transformation branches, categories are used to indicate the main energy conversion modules such as electric generation, charcoal making and oil refining and to organize the various processes and output fuels in each moduleA Transformation branch representing an energy industry or sector, such as electricity generation, oil refining, district heating, charcoal production, or electricity transmission and distribution . Note that in the Transformation tree, unlike the demand tree, you cannot have flexible levels of data disaggregation. In the Resource branches, categories are used to organize resource into primary resources and secondary fuels. Categories are also used in cases where you choose to disaggregateTo break something down into sub-categories (e.g. during end-use analysis of energy demands). your primary resourceA fuel that has not been converted or processed such as coal, crude oil, hydropower, solar, wind, etc. accounting analysis.

![](../assets/images/NewButtons/Tree/FolderGreen.png) Category With Aggregate Energy Intensity branches are used to indicate a category branch at which energy intensities are specified at one level up from the actual energy-using devices.  These branches are useful in three main cases:

1) where you have energy intensity data for an end-use, and only have fuel share data (not intensity data) for the fuels and devices within the end-use,

2) where you have devices that use more than one fuel, and

3) where you wish to conduct a [Useful Energy Demand Analysis](../05%20-%20Demand/Useful_Energy_Analysis.md).

Technology branches are used In the Demand branches to represent final energy consuming devices, and hence are uniquely associated with a particular fuelSomething combusted, or otherwise used to produce energy . They are also used in the Transformation branches to indicate processes: the individual technologies or groups of technologies within a module that are responsible for converting or transporting energy forms, such as a particular electric power plant or an oil refinery.  Transformation processes are represented by a gray cog wheel icon (![](../assets/images/NewButtons/Tree/technology.png)), while in the Demand branches, three different types can be created, depending on the kind of analysis to be conducted:

![](../assets/images/NewButtons/Tree/technology.png) [Activity Level Technologies](../05%20-%20Demand/Activity_Level_Analysis.md) are used when energy consumption is calculated as the product of an activity level and an annual energy intensity.

![](../assets/images/NewButtons/Tree/Stock.png) [Stock Technologies](../05%20-%20Demand/Stock_Analysis.md) are used when energy consumption is calculated by analyzing the turnover of stocks of energy-using devices.

![](../assets/images/NewButtons/Tree/vehicle.png) [Transport Technologies](../05%20-%20Demand/Transport_Analysis.md) are used when energy consumption is calculated by analyzing the stock turnover of vehicles.

![](../assets/images/NewButtons/Tree/fire.png)Fuel branches are represented by a small sun. In the Transformation tree they indicate the various output fuels produced by each Transformation module. In the Resource tree, they indicate the primary resources and secondary fuels produced, imported and exported in your areaThe energy system being studied. In the Stock Change and Statistical Differences branches they represent fuels for which you can specify base year stock change and statistical differences.

![](../assets/images/NewButtons/Tree/Effects.png)  Environmental Loading branches are represented by a gray cloud.  These can be specified wherever a fuel is combusted (e.g. below Demand technology branches and below Transformation feedstock fuels and auxiliary fuels).  They can also be specified under the Non-Energy branches, where they are used to specify emissions of pollutants from sectors not included in your main energy analysis.

![](../assets/images/NewButtons/Tree/In.png) Indicator branches are used to calculate additional user-defined results.  They work in a similar fashion to Key assumption branches but are only calculated after all other results.  Therefore, unlike other variables, Indicators can include non-lagged references to LEAP's results variables.

Some restrictions exist on where you can create different branches. For example, you cannot move branches between the four major categories (Key Variables, Demand, Transformation, and Resources) and in most cases you cannot mix branches with different icons at a single level. These restrictions affect the various [Tree editing options](Editing_the_Tree.md) that let you add, delete, copy, paste, and move branches.