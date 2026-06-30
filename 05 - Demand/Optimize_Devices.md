---
Source: https://leap.sei.org/help24/Demand/Optimize_Devices.htm
---

# Optimize Devices

See also: [Analysis View](../02%20-%20Views/Data_View.md) , [Demand Analysis](Demand.md)

Used only when conducting full energy system optimization modeling and only available at category branches that specify a useful energy intensity (![](../assets/images/NewButtons/Tree/FolderGreen.png)).  A Yes/No switch used to indicate if the activity level shares of the technologies below the category branch (![](../assets/images/NewButtons/Tree/Technology%20Green.png)) should be calculated by LEAP's energy system optimization calculations.   If set to **No**, you will need to enter the activity level data exogenously.  If set to **Yes**, additional variables will appear at the technology branches with which you can specify the [capital costs](Capital_Cost.md), [fixed O&M costs](Fixed_OM_Cost.md) and [variable O&M costs](Variable_OM_Cost.md), etc. of each device, and the number of devices per activity level. You can also specify constraints that specify the [minimum shares](Minimum_Share.md) and [maximum shares](Maximum_Share.md) for the activity levels of each technology and the [maximum annual change in the share](Maximum_Annual_Share_Change.md). You will also need to specify the [unit capacity](Unit_Capacity.md) of each device and its [lifetime](Lifetime.md).