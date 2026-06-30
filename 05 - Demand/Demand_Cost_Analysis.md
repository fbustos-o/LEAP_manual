---
Source: https://leap.sei.org/help24/Demand/Demand_Cost_Analysis.htm
---

# Demand Costs

See also: [Demand Analysis](Demand.md), [Analysis View](../02%20-%20Views/Data_View.md)

Use the Demand Costs data tab to specify the non-fuel costs of your demand scenarios (capital, O&M and administrative). These costs are used in LEAP's overall cost-benefit calculations to help evaluate your policies and measures. You can specify costs for any demand branchAn item on the tree. Different types of branches are represented by different icons on the tree . Typically, you specify costs for each demand technology (![](../assets/images/NewButtons/Tree/technology.png)), but you can also specify costs at higher levels of aggregation (for example the costs of sectoral demand side management programs). Bear in mind that for a comparative analysis of scenarios, you need only enter costs for branches where activities or energy intensities change compared to your baseline.

Note: Demand Costs are only available if the Costs checkbox is checked on the Scope tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen.

LEAP provides four different methods for specifying demand costs:

1. Costs Per Activity: This is the default costing method. It allows you to specify non-fuel costs per unit of activity (e.g. costs per household for residential sector measures or costs per passenger-km in the transport sector). This method is simple to implement because it requires no additional data (other than a cost and an activity level). In cases where your activity level variable is not the same as the physical number of devices affected the cost values you enter should be the annual cost per device multiplied the number of devices per activity (for example the number of light bulbs per household). Alternatively, you may wish to use the Cost per Device methodology described below.

The value you enter is used in LEAP's calculations in the following way:  
Costs, t = Cost per Activitys, t x Activity Levels, t

2. Costs Per Device Sold: If you selected the [Stock Analysis](Stock_Analysis.md) or [Transport Analysis](Transport_Analysis.md) methods for a Technology (![](../assets/images/NewButtons/Tree/technology.png)), then you will also be able to use this second costing method and enter costs per device sold. This method lets you track the costs of new and replacement devices, and for this reason tends to be a more accurate (although more data intensive) approach than the above method.

The value you enter is used in LEAP's calculations in the following way:  
Costs, t = Cost per Device Solds, t x Devices Solds, t

3. Total Costs: In some cases you simply want to specify a total annual cost at a demand branch (i.e. one that is not per activity level, per unit saved or per device sold). In these situations, choose the Total Cost method and enter the total annual costs in the expression. Use LEAP's [AnnualizedCost](../18%20-%20Expressions/AnnualizedCost.md) function when you want to build-up this value by annualizing (levelizing) a capital cost. This cost method can be particularly useful when specifying overall program or administrative costs of programs at higher levels branches in your analysis.
4. Cost of Saved Energy (CSE) expresses the incremental cost of saving energy in a device relative to the energy used in some baseline scenario. The CSE method lets you directly compare the costs of demand side energy efficiency investments with those of conventional energy supply investments and is most appropriately used when you are changing the energy intensity of a particular device in a given scenario to reflect efficiency improvements, rather than switching from one branch to another.  
     
   ![](../assets/images/NewScreens/CSEBox.png)
5. When specifying a CSE you will need to enter the cost per unit energy saved relative to either Current Accounts or another scenario. Bear in mind that energy intensities may change over time even in a policy neutral scenario, so you should normally specify CSE costs relative to some baseline scenario. However, if you expect energy intensities to be constant over time then you can also specify CSE costs relative to Current Accounts intensities. When you pick the CSE method, a special screen will pop up (shown right) in which you can select the units (currency per unit of energy saved) and the scenario against which you will be specifying the costs.

The CSE value you enter should represent the annual average cost per unit of energy saved.  
Use LEAP's [AnnualizedCost](../18%20-%20Expressions/AnnualizedCost.md) function when you want to build-up this value by annualizing (levelizing) a capital cost. You can also include operations & maintenance (O&M) and administrative costs in the CSE.

The CSE value you enter is used in LEAP's calculations in the following way:

1. * When costs are specified relative to another scenario:

Costs, t = CSEs, t * Activity Levels, t * (Energy IntensityBL, t - Energy Intensitys, t)

where s is the current scenario, BL is the baseline scenario, and t is the year.

1. * When costs are specified relative to the Current Accounts intensity

Costs, t = CSEt * Activity Levels, t * (Energy Intensity0 - Energy Intensitys, t)

Note that CSE costs will be zero in the base year by definition since changes in energy intensity occur only in future scenario years.