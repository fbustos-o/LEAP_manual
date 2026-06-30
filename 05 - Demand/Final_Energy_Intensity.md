---
Source: https://leap.sei.org/help24/Demand/Final_Energy_Intensity.htm
---

# Final Energy Intensity

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Activity Analysis](Activity_Level_Analysis.md), [Activity Level](Activity_Level.md), [Total Energy](Total_Energy.md)

Final energy intensity is the final energy consumption at a specific branch/variable per unit of activity level.

Final energy intensities are typically defined at the lowest level technology branches (![](../assets/images/NewButtons/Tree/technology.png)), but can also be defined at the next level up, when specifying a branch of type Category with Energy Intensity (![](../assets/images/NewButtons/Tree/FolderGreen.png)).

Note that some activity level data have units that have no time dimension such as households. In these cases the energy intensity variable is implicitly entered as the energy consumed per unit of activity per year.   Other activity level data do have an annual time dimension such as passenger-kms traveled per year or tonnes of cement produced per year.  In these cases, the energy intensity variable is implicitly entered as energy per activity unit.  LEAP does not explicitly distinguish between these two situations.  The onus is on the user to ensure that the result of multiplying the activity level and energy intensity variable is the annual energy consumption in that branch.

## Units

LEAP lets you enter energy intensities for technologies in energy, mass or volume units. It will also automatically convert your data from one unit to another. Note that when the fuel is a pure energy form such as electricity, the units must be an energy unit.

## Time-Sliced Energy Data

In normal circumstances, energy demand data are specified annually.  The seasonal and time-of-day variations in energy demands are specified later on by specifying the load shape for the entire electric system in each Transformation module.  However, on the [General: Settings: Loads](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Loads) screen you can instead choose to specify the load shapes of each individual demand device.  If you have chosen this approach then the Demand Branch Properties screen will show additional options that let you specify how energy consumption in these devices varies by [time slice](../16%20-%20Supporting%20Screens/Time_Slices.md).

The three options are:

* Annual Energy:  If you choose this approach you can enter annual energy consumption data either as an energy intensity or as total energy per device.  You will also need to specify data in a separate [Load Shape](Load_Shape.md) variable, which is displayed in the Current Accounts scenario.
* Time Sliced (Energy Per Slice): If you choose this approach you can directly specify energy consumption in each time slice.
* Time Sliced (Power Per Slice): If you choose this approach you can directly specify the average power consumption in each time slice.  LEAP will automatically multiply this data by the duration (in hours) of each time slice in order to calculate the energy consumption in each time slice.