---
Source: https://leap.sei.org/help24/Demand/Demand_Properties_Wizard.htm
---

# Demand Branch Properties

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Final Energy Demand Analysis](Final_Energy_Demand_Analysis.md), [Useful Energy Demand Analysis](Useful_Energy_Analysis.md), [Activity Analysis](Activity_Level_Analysis.md), [Stock Analysis](Stock_Analysis.md), [Transport Analysis](Transport_Analysis.md)

![](../assets/images/NewScreens/Demand%20Branch%20Properties.png)

Use this screen to edit the properties (name, type, etc.) of a demand branch.  Note that some of the options shown here (e.g. Energy Demand, Fuel) will only appear when relevant.  The options displayed depend on the type and properties of the branch.

## Types of Demand Branches

Demand branches can be the following types:

![](../assets/images/NewButtons/Tree/folder.png) Category branches are used mainly for organizing the other branches into hierarchical data structures. These branches only contain data for [Activity Levels](Activity_Level.md), [Costs](Demand_Cost_Analysis.md) and any [User Variables](../16%20-%20Supporting%20Screens/User_Variables.md).

![](../assets/images/NewButtons/Tree/FolderGreen.png) Category With Energy Intensity branches are used to indicate a category branch at which energy intensities are specified at one level up from the actual energy-using technologies.  These types of branches have three additional options shown as check boxes:

* **Useful Energy Analysis:** Switch this option on if you want to specify a useful energy intensity at the category level along with efficiency data at the device level. With this option switch on, you can optional choose to switch on the following option:
* **Final Energy Intensities in Current Accounts:** This option allows you to specify historical final energy intensity data (i.e. fuel consumption) at the end-use level in Current Accounts along with fuel share data for the devices below the end-use. LEAP will calculate the implied useful energy intensity and you can make projections of useful energy intensities in each scenario. Leave the box unchecked to directly specify useful requirements (i.e. the service demand) in both Current Accounts and scenarios. In either case you will always enter the useful demand for other scenarios.
* **Device Can Be Optimized:** Switch on this option if you want to use optimization calculations to calculate the share of devices in [full energy system optimization](../21.2%20-%20Optimization/OptimizationIntroduction.md) calculations.  Once switched on, in full energy system optimization scenarios you will see the additional [Optimize Devices](Optimize_Devices.md) variable for the demand category branch which can be switched off or on in different regions and scenarios. You will also see  all of the various additional variables used by the optimization calculation such as [Minimum Share](Minimum_Share.md), [Unit Capacity](Unit_Capacity.md), etc.

![](../assets/images/NewButtons/Tree/technology.png) Technology with Energy Intensity branches are used to specify final energy consuming technologies, and hence when choosing this type of branch you will also need to select the fuel consumed.  Use this type of technology branch when you want to project energy consumption as the product of an activity level and an energy intensity.

When conducting a useful energy demand analysis, you can optionally specify a co-product that is produced when the technology operates. For example, a demand for heat in buildings could be met using a combined heat and power (CHP) unit that consumes natural gas but also produces electricity as a coproduct.  Note that only technologies created below a green category branch (![](../assets/images/NewButtons/Tree/FolderGreen.png)) can have co-products in which a useful energy analysis has been enabled can have a co-product.  If you specify a co-product, an additional variable (tab) will appear in the main data entry screen in which you can specify the co-product efficiency. Note that the sum of the efficiency and co-product efficiency must be less than or equal to 100%.

![](../assets/images/NewButtons/Tree/Technology%20Red.png) Technology with Total Energy branches are used to specify final energy consuming technologies, and hence when choosing this type of branch you will also need to select the fuel consumed.  Use this type of technology branch when you want to project energy consumption directly by entering data on the total energy consumed.  In other words, this type of branch ignores any data entered in the Activity level variable.

![](../assets/images/NewButtons/Tree/Stock.png) Stock Analysis branches are used to specify the data needed in a stock-turnover calculation.  Using this approach, energy consumption is calculated by analyzing the current and projected future stocks of energy-using devices and the annual energy intensity of each device (defined as energy per device).

![](../assets/images/NewButtons/Tree/vehicle.png) Transport Analysis branches are used to specify the data needed in a transport stock turnover calculation.  In this approach energy consumption is calculated as the product of the number of vehicles, the annual average mileage (i.e. distance traveled per vehicle) and the fuel economy of the vehicles (e.g. liters per km or 1/MPG).

Note: in general you cannot mix branch types in immediately neighboring branches. For example, category and technology branches cannot be placed together within the same tree folder. Because of this restriction, you sometimes will not be able to change the type of an existing branch if it already has neighboring branches.  The exception to this rule is that both types of category branches can be placed next to each other.

## Technology Branch Icons

**I**f fuel icons are enabled within the [Fuels screen](../16%20-%20Supporting%20Screens/Fuels.md), technology branches will be displayed in the tree with the fuel icon corresponding to the fuel consumed within that technology. This is similar to how Transformation technologies and feedstock, auxiliary, and output fuels are displayed. When fuel icons are disabled, technologies will be shown using one of the default technology icons shown above.

## Tips for Specifying Branch Names

When specifying the name of a branch in most cases you simply need to type a name in the Name box. In order to avoid conflicts with LEAP's built-in mathematical functions, some names are not allowed. LEAP will automatically check the name you enter and alert you to any conflicts.  Note that the **OK** button will be disabled until you have entered a valid name.

When creating a technology branch you will often simply want to name the branch the same as its associated fuel.  To avoid extra typing, you can first choose the fuel from its selection box and LEAP will then use that as the branch name.  To quickly select a fuel type the first few letter of its name.  For example, type "el" to quickly select electricity.  After selecting a fuel you can always edit or override the branch name by editing the text in the name box.

## Special Properties When Energy Demand Data is Time Sliced

In normal circumstances, energy demand data are specified annually.  The seasonal and time-of-day variations in energy demands are specified later on by specifying the load shape for the entire electric system in each Transformation module.  However, on the [General: Settings: Loads](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Loads) screen you can instead choose to specify the load shapes of each individual demand device.  If you have chosen this approach then the Demand Branch Properties screen will show additional options that let you specify how energy consumption in these devices varies by [time slice](../16%20-%20Supporting%20Screens/Time_Slices.md).

The three options are:

* Annual Energy:  If you choose this approach you can enter annual energy consumption data (either as an energy intensity or as total energy per device. You will also need to specify data in a separate [Load Shape](Load_Shape.md) variable, which is displayed in the Current Accounts scenario.
* Time Sliced (Energy Per Slice): If you choose this approach you can directly specify energy consumption in each time slice.
* Time Sliced (Power Per Slice): If you choose this approach you can directly specify the average power consumption in each time slice.  LEAP will automatically multiply this data by the duration (in hours) of each time slice in order to calculate the energy consumption in each time slice.