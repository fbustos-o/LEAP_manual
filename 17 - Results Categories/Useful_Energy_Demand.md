---
Source: https://leap.sei.org/help24/Results_Categories/Useful_Energy_Demand.htm
---

# Useful Energy Demand

**See also:** [Results View](../02%20-%20Views/Results_Screen.md), [Final Energy Demand](Net_Final_Fuel_Demand.md)  
Result Type: Demand

This displays the useful demand for energy in one or more demand branches.

Useful energy demand is the part of [final energy demand](Net_Final_Fuel_Demand.md) available to do useful work (heating, cooling, cooking, etc.) after losses within final energy consuming devices.

Useful energy demand is generally smaller than final energy demand due to losses in demand devices. However, devices like refrigerators and heat pumps typically have efficiencies greater than 100% because they consume both electricity and free/ambient energy energy and produce useful energy in the form of cooling or heating.  Thus, for these devices useful energy demand may be greater than final energy demand.

To keep data requirements down to a minimum, useful energy demand is, by default, only calculated in branches in which you have are conducting a [useful energy analysis](../05%20-%20Demand/Useful_Energy_Analysis.md).

If you want to calculate useful energy demands across all demand branches,  go to the [Settings: Scope](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Scope) screen and switch on the option marked **Calculate Useful Energy for All Demands.** Once you do that an additional variable will appear for all demand technologies marked **Energy Efficiency**,which is used to calculate Useful Energy Demands.