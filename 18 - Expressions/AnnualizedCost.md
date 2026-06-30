---
Source: https://leap.sei.org/help24/Expressions/AnnualizedCost.htm
---

# AnnualizedCost

## Syntax

AnnualizedCost(Capital Cost, Life, Rate, O&M Cost) or  
AnnualizedCost(Capital Cost, Life) or

## Summary

Calculates a real annualized cost that is incurred each year. Annualized costs are calculated from a total capital cost, the lifetime of the device (or loan), and the interest rate charged for the loan. Capital costs are annualized using the Capital Recovery Method, following a similar method to that used for the [PMT function  in Microsoft Excel](http://office.microsoft.com/en-us/excel-help/pmt-function-HP010342769.aspx).  An optional annual operating and maintenance (O&M) cost can also be added to the annualized capital costs. The full formula for calculating annualized cost is given as follows:

![](../assets/images/Expressions/AnnualizedCost2.png)

## Parameters

* Capital Cost: the total (i.e. not annualized) capital cost. In cases where your demand data specifies the physical number of end-use devices enter the costs of each device. In other cases, where the activity unit is not a device (e.g. in households using multiple light bulbs) enter the capital cost per unit of activity. In other words multiply, the cost per device by the number of devices per activity (e.g. light bulbs per household).
* Life: a whole number of years - the lifetime of the device or the period of loan on the capital cost as appropriate.  Note, when lifetime is zero the capital cost is not annualized, so the Rate term is ignored.  
  In other words, when Life=0:    
  AnnualizedCost = CapitalCost + O&MCost
* Rate: the rate charged on the loan for the capital cost (defaults to the study discount rate).  Entered as a decimal fraction. Note that when the interest rate is zero, annualized cost is calculated as follows:  
  When Rate=0:  
  AnnualizedCost = (CapitalCost/Life) + O&MCost
* O&M Cost: Any annual recurring O&M or administrative costs.  Note: when specifying demand costs as a part of LEAP's social cost-benefit calculations, do not include fuel costs.  Fuel costs are handled under the Resource branches.

## Examples

Annualizing a capital cost of $100 over a five-year period at an interest rate of 5% with no O&M costs, yields an annualized cost of $23.10 as follows:

AnnualizedCost(100, 5, 0.05, 0) = 23.10

Note the rate (0.05) could also be written as "5%"

Annualizing a capital cost of $100 over a one period at an interest rate of 5% with no $10 O&M costs, yields an annualized cost of $105+$10 = $115 as follows:

AnnualizedCost(100, 1, 0.05, 10) = $115