---
Source: https://leap.sei.org/help24/Expressions/Yes.htm
---

# Yes

## Syntax

Yes

See also: [Operators](Operators.md), [No](No.md),  [AND](AND.md), [OR](OR.md), [NOT](opNot.md)

## Summary

Returns a value of 1.  Equivalent to [True](True.md).

## Controlling Optimization

When used with the [Optimize](../08%20-%20Transformation/Optimize.md) and [Energy System Optimization](../08%20-%20Transformation/Energy_System_Optimization.md) variables to switch on module level or energy system optimization, the **Yes** function can take optional additional parameters,  which are used to select a specific solver, to control perfect foresight or limited foresight optimization, and to switch major optimization options on and off.

In this context, the allowed extended syntax is as follows:

Yes(Solver)

Yes(Solver,  Year1, Year2, ..YearN)

Yes(Solver,  Presolve, HSD, Extra NEMO Parameters,  Year1, Year2, ..YearN)

These additional parameters are only allowed when specifying the [Optimize](../08%20-%20Transformation/Optimize.md) and [Energy System Optimization](../08%20-%20Transformation/Energy_System_Optimization.md) variables.

## Optional Parameters

* **Solver:** The optional solver parameter is the name of the solver to use with NEMO.  Allowable values are: Gurobi, CPlex, XPress, MOSEK, Cbc, HiGHS, or GLPK.  Solver labels are not case sensitive. If the solver parameter is omitted, LEAP will instruct NEMO to use the fastest available solver installed on your PC (assumed to be Gurobi, CPLEX, XPress, and then HiGHS in that order).  When specifying a solver, if that solver is not installed, the optimization calculation will fail and generate an error.   
    
  For best calculation performance and maximum portability of your model, it is best to NOT specify a particular solver.  However, this may occasionally be useful, for example if you want to check that different installed solvers are producing the same results. In some cases, different solvers may yield slightly different results (most often due to the solver being designed to speed up calculations). Note also that by using this function you can use different solvers when calculating different scenarios.     
    
  The commercial solvers CPLEX, GUROBI and XPress must be purchased and installed separately from LEAP and NEMO. MOSEK is installed with NEMO but you must have a properly purchased and installed license to use it. Use the orange  Exp button (![](../assets/images/NewButtons/Exp%20Button.png)) in the data entry table to quickly select a solver from among those installed on your PC.

* **Presolve:** This optional 2nd parameter must be set to yes (1) or no (0) and is used to switch presolve off or on. Presolve is on by default.
* **HSD:** This optional 3rd parameter must be set to yes (1) or no (0). It is used to enable Homogeneous self-dual barrier optimization (HSD) in Gurobi and CPLEX.  It has no effect for other solvers. HSD methods can provide stronger detection of infeasible or unbounded models, or models with numerical trouble, and they generally produce more robust and stable results with ill-conditioned models (models in which small changes in the inputs cause large changes in the solution). However, for well-conditioned models, HSD can be slower than standard methods. HSD is always on in the MOSEK solver, and HSD is off by default.  Note: if specifying a value for HSD, you must also specify a value for presolve.
* **Extra NEMO Parameters:** This optional 4th parameter is simply a text string, which can be used to pass additional parameters to NEMO. Note: if specifying extra NEMO parameters you must also specify values for presolve and HSD.

* **Limited Foresight Years:** The **Yes** function can also take a list of years to enable limited foresight optimization. If no years are specified, NEMO will use perfect foresight optimization. The list of years must be in ascending chronological order and must be specified after any other parameters to the function. Any years before the first scenario year or after the end year will be ignored. Each calculated year will be grouped based on whether it occurs before or on each grouping year.  
    
  With perfect foresight optimization, all years are optimized at the same time. With limited foresight optimization, years are divided into groups, each of which is separately optimized. Results from each group provide the starting conditions for the next group.   
    
  With both limited foresight and perfect foresight optimization, you can elect to calculate selected years only, using the **Results Every** option on the [Settings:Years](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#Years) screen. Note that limited foresight optimization requires NEMO v2.2 or later.

## Examples for Controlling Optimization

* **Yes**: Switches on perfect foresight optimization and instructs NEMO to use the fastest available solver.
* **Yes(CPLEX)**: Switches on perfect foresight optimization and instructs NEMO to solve using the CPLEX solver.
* **Yes(Gurobi, true, true)**: Solves with Gurobi and uses both presolve and HSD (Homogeneous self-dual barrier optimization).
* **Yes(2030, 2040)**: Switches on limited foresight optimization.  Calculated years will be put into three groups: (1) any calculated years up to and including 2030, (2) any calculated years from 2031 to 2040, (3) Any calculated years after 2040.
* **Yes(HIGHS, 2030, 2040):** Limited foresight optimization using the HiGHS solver.
* **Yes(Gurobi, false, true, 2030, 2040):** Limited foresight optimization using the Gurobi solver, with presolve switched off and HSD switched on.

Note: for compatibility with older versions of LEAP, you can also use the deprecated [NEMO](NEMO.md) function, which takes the same parameters as the **Yes** function.