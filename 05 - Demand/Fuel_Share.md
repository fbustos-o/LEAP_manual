---
Source: https://leap.sei.org/help24/Demand/Fuel_Share.htm
---

# Fuel Share

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Useful Energy Demand Analysis](Useful_Energy_Analysis.md)

Fuel shares are the percentage share of final energy at an end-use consumed by one of the device branches below it. Notice that when the efficiencies of devices are not all 100%, then fuel share is not identical to activity level share. For example, consider an end-use such as heating that can be met by either natural gas boilers at 80% efficiency or electric boilers at 100% efficiency. If each boiler is sized to deliver the same amount of heat, and each is installed in 50% of homes, then the activity level shares of each will be 50%, but the fuel shares will be as follows: (Natural gas = 55.6%, electricity = 44.4%) To see why, look at the table below.

![](../assets/images/Demand/FuelShareCalc.gif)

Fuel share data are only required for Current Accounts when conducting a [useful energy demand analysis](Useful_Energy_Analysis.md) (![](../assets/images/NewButtons/Tree/FolderGreen.png)) if you chose to specify final energy intensities in Current Accounts on the Demand branch properties screen. They are not required if you choose to specify useful energy intensities directly in Current Accounts. Fuel shares are always entered for the technology branches (![](../assets/images/NewButtons/Tree/Technology%20Green.png)).