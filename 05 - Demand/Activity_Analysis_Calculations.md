---
Source: https://leap.sei.org/help24/Demand/Activity_Analysis_Calculations.htm
---

# Activity Analysis Calculations

For an activity analysis, calculations differ depending on whether you are conducting a final or useful energy demand analysis.

## Final Energy Demand Analysis

In a final energy demand analysis, energy demand is calculated as the product of the total activity levelA measure of social and economic activity. When used in LEAP's Demand analysis, activity levels are multiplied by energy intensities to yield overall levels of energy demand and energy intensityThe average energy consumption of some device or end-use per unit of activity. at each given technology branchAn item on the tree. Different types of branches are represented by different icons on the tree (![](../assets/images/NewButtons/Tech%20Gray.png)). Energy demand is calculated for the Current AccountsThe starting data for all scenarios. The Current Accounts can include data for just a single Base Year, or data for multiple historical years between the Base Year and one year before the First Scenario Year. year and for each future year in each scenarioA self-consistent story line of how a future energy system might evolve over time in a particular socio-economic setting and under a particular set of policy conditions. . In other words:

 Db,s, t = TAb,s, t x EIb,s, t

Where D is energy demand, TA is total activity, EI is energy intensity, b is the branch, s is scenario and t is year (ranging from the base yearThe first historical year of a LEAP analysis. [0] to the end year). Note that all scenarios evolve from the same Current Accounts data, so that when t=0, the above equation can be written as:

 Db,0 = TAb,0 x EIb,0

The energy demand calculated for each technology branch is uniquely identified with a particular fuelSomething combusted, or otherwise used to produce energy . Thus, in calculating all technology branches, LEAP also calculates the total final energy demand from each fuel.

The total activity level for a technology is the product of the activity levels in all branches from the technology branch back up to the original Demand branch. In other words:

 TAb,s, t = Ab',s, t x Ab'',s, t x Ab''',s, t x ...

Where Ab is the activity level in a particular branch b, b' is the parent of branch b, b'' is the grandparent, etc. Note that those branches marked as having "No data" as well as the top level "Demand" branch are treated as having an activity level of 1. The activity level values of other branches with percentage units (e.g. percent shares or percent saturation) are always divided by 100 to yield a fractional value from zero to one in the calculations.

## Useful Energy Demand Analysis

In a useful energy demand analysis, energy intensities are specified, not for a technology, but at one level up, at a category with aggregate energy intensity type branch.  To distinguish these from standard category branches (![](../assets/images/NewButtons/Tree/folder.png)) they are marked as folders with a green tab (![](../assets/images/NewButtons/Tree/FolderGreen.png)) and the technologies below them are also colored green (![](../assets/images/NewButtons/Tech%20Green.png)).  When using this method, in Current Accounts you specify final energy intensities at category level and fuel shares and efficiencies for each technology branch below (![](../assets/images/NewButtons/Tech%20Green.png)). These data are used calculate the overall useful energy intensity for the aggregate energy intensity branch and the activity shares for each technology as follows:

For each technology branch:

 UEb,0 = EIAG,0 x FSb,0 x EFFb,0  
Where b = 1..B

Where EIAG,0 is the final energy intensity in aggregate energy intensity branch, UE is the useful energy intensity in a technology branch b, FS is its fuel share, EFF is its efficiency, and b is one of B technology branches.

The useful intensity of the aggregate energy intensity branch is the sum of the useful intensities for each technology branch:

 UEAGG,0 = Sumb = 1.. B(UEb,0)

The activity share (i.e. the share of the number of technologies, rather than the fuel share) is the product of the fuel share and efficiency of each technology b:

 ASb,0 = UEb,0 / UEAGG,0

Where AS is activity share.

The following example illustrates this calculation. Consider an aggregate energy branch with a final intensity of 100 GJ per activity (i.e. 100 GJ of fuel), and 2 technologies each of which has a 50% fuel share. The electricity technology has an efficiency of 100% and the natural gas technology has an efficiency of 70%. Thus, the useful energy intensities of the technologies are 100 * 50% *100% = 50 GJ/activity and 100 * 50% * 70% = 35 GJ/activity respectively, and the activity shares are 50/85 = 59% and 35/85 = 41% respectively.

![](../assets/images/Demand/UsefulCalc.gif)

* In scenarios, you enter expressions to independently project the Current Accounts values calculated above for the useful energy intensity of the aggregate energy intensity branch, the technology activity shares and their efficiencies. The final energy intensity for each technology is given by:

 EIb,s, t = UIAGG,s, t x ASb,s, t / EFFb,s, t

Overall energy demand for each technology is calculated in the same way as for a final energy demand. In other words:

 Db,s, t = TAb,s, t x EIb,s, t

Note: when specifying aggregate energy intensities, but not conducting useful energy analysis, the above equations still hold and all efficiencies are set equal to 100%.