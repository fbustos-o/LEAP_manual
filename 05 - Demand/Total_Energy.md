---
Source: https://leap.sei.org/help24/Demand/Total_Energy.htm
---

# Total Energy

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Activity Analysis](Activity_Level_Analysis.md), [Activity Level](Activity_Level.md), [Final Energy Intensity](Final_Energy_Intensity.md)

Total Energy is the total final energy consumption at a specific branch/variable.  Total energy is distinguishable from Final Energy Intensity by the fact that energy data is entered directly: that is it is not specified as the product of an [activity level](Activity_Level.md) and an [energy intensity](Final_Energy_Intensity.md).

Total Energy data is defined at the lowest level technology branches. Technology branches that are defined with Total Energy data are indicated by red technology icons (![](../assets/images/NewButtons/Tree/Technology%20Red.png)), while the folder above these technologies is indicated by a red tab (![](../assets/images/NewButtons/Tree/FolderRed.png)).

## Units

LEAP lets you enter total energy data for technologies in energy, mass or volume units. LEAP will also automatically convert your data from one unit to another.  Note that when the fuel is a pure energy form such as electricity, the units must be an energy unit.

## Time-Sliced Energy Data

In normal circumstances, energy demand data are specified annually.  The seasonal and time-of-day variations in energy demands are specified later on by specifying the load shape for the entire electric system in each Transformation module.  However, on the [General: Settings: Loads](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Loads) screen you can instead choose to specify the load shapes of each individual demand device.  If you have chosen this approach then the Demand Branch Properties screen will show additional options that let you specify how energy consumption in these devices varies by [time slice](../16%20-%20Supporting%20Screens/Time_Slices.md).

The three options are:

* **Annual Energy:**  If you choose this approach you can enter annual energy consumption data either as an [energy intensity](Final_Energy_Intensity.md) or as [total energy](Total_Energy.md) per device.  You will also need to specify data in a separate [Load Shape](Load_Shape.md) variable, which is displayed in the Current Accounts scenario.
* **Time Sliced (Energy Per Slice):** If you choose this approach you can directly specify energy consumption in each time slice.
* **Time Sliced (Power Per Slice):** If you choose this approach you can directly specify the average power consumption in each time slice.  LEAP will automatically multiply this data by the duration (in hours) of each time slice in order to calculate the energy consumption in each time slice.