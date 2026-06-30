---
Source: https://leap.sei.org/help24/Expressions/LoanPayment.htm
---

# LoanPayment

## Syntax

LoanPayment(Capital Cost, First Year, Loan Term)  
  
or  
  
LoanPayment(Capital Cost, First Year, Loan Term, Interest Rate)

## Description

Calculates annual payments on a loan, from data on total capital cost, year of loan, the term of the loan (enter 0 if there is no loan), and the interest rate charged for the loan.

## Parameters

* **Capital Cost:** the principle of the loan.
* **First Year:** the first year of the loan.
* **Loan Term:** a whole number of years - the period of loan on the capital cost.  Enter 0 if there is no loan.
* **Interest Rate (optional):** the rate charged on the loan for the capital cost.  Enter as either a fraction (e.g., 0.05) or a percent (e.g., 5%).  Defaults to the study discount rate if not included.  Change the study discount rate on the General: Parameters: Costing screen.

## Example

LoanPayment(1000000, 2005, 15, 5%)

Calculates annual payments of $96,342.29, starting in 2005 for a 15-year loan of $1,000,000 at an interest rate of 5%.