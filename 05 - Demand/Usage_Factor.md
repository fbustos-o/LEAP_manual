---
Source: https://leap.sei.org/help24/Demand/Usage_Factor.htm
---

# Usage Factor

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Stock Analysis](Stock_Analysis.md), [Marginal Final Energy Intensity](Energy_Intensity.md)

This variable is used only in non-transport device stock turnover models.  It is a simple multiplicative factor (with a default value of one) that is applied to the average intensity of all devices of any vintage in each year of a calculation. It allows users to distinguish between device technical specifications which depend on stock turnover and the usage of the device which is likely to depend more on socio-economic factors.  For example, you might use this factor to simulate how average household heating and cooling usage increases year-on-year as incomes increase, and independently of the introduction of new building efficiency standard (which are modeled via the [marginal final energy intensity](Energy_Intensity.md) variable).