---
Source: https://leap.sei.org/help24/Optimization/Solvers_Supported_by_LEAP_and_NEMO.htm
---

# Solvers Supported by LEAP and NEMO

See also: [Setting Up Optimization in LEAP](Setting_Up_Optimization_in_LEAP.md)

## Supported Solvers

The following solvers are currently supported by LEAP and NEMO.  We may add support for additional solvers in future.

* **Cbc** is a free and open-source mixed integer linear programming solver. Cbc is included when you install NEMO. As of early 2020, Cbc is being actively developed. [Cbc web site here](https://github.com/coin-or/Cbc).
* **HIGHS** is a free and open-source linear programming (LP), mixed-integer programming (MIP) and quadratic programming (QP) solver It is freely available under the MIT open-source licence and is installed by default as part of NEMO. [Website here.](https://highs.dev)
* CPLEX is a mathematical programming solver for linear programming, mixed-integer programming and quadratic programming developed by IBM and sold commercially. CPLEX must be obtained separately from LEAP and NEMO. Prices depend on the type of user and can be US$9000 or more for a single user. Licenses may be available at low or no cost to selected academic organizations. [Contact IBM for a quotation. Web site here.](https://www.ibm.com/analytics/cplex-optimizer)
* **GUROBI** is a commercial optimization solver for linear programming, quadratic programming, quadratically constrained programming, mixed integer linear programming, mixed-integer quadratic programming, and mixed-integer quadratically constrained programming. It is developed and sold commercially. GUROBI must be obtained separately from LEAP and NEMO. Prices depend on the type of user and can be US$10000 or more for a single user. Licenses may also be available at low or no cost to selected academic organizations. [Contact Gurobi for a quotation. Web site here.](https://www.gurobi.com/)  As of NEMO 2.3 and later, Gurobi is now distributed with NEMO but to enable its functionality you must still purchase a license and install a license file provided by the developers.
* **MOSEK** is a commercial optimization solver designed to solve large-scale mathematical optimization problems. It is developed and sold commercially. MOSEK is distributed with NEMO but to enable its functionality you must still purchase a license and install a license file provided by the developers. Prices depend on the type of user, starting at $1950 for a single user plus an annual maintenance fee of $488. Licenses may also be available at low or no cost to selected academic organizations. [Contact MOSEK for a quotation. Web site here.](https://www.mosek.com/)
* **FICO** XPress is a commercial optimization solver. Standard capabilities include scalable high-performance solvers and algorithms, flexible modeling environments, rapid application development, comparative scenario analysis and reporting capabilities, for on-premises and cloud installations.  XPress is developed and sold commercially and must be obtained separately from LEAP and NEMO. [Contact FICO for a quotation. Web site here.](https://www.fico.com/en/products/fico-xpress-optimization)
* **GLPK**: The GNU Linear Programming Kit is intended for solving linear and mixed integer programming  and other related problems. This solver is free and open source and is included when you install NEMO. While adequate for small problems, GLPK is slow in solving larger problems. It has not been updated since 2018 and as of early 2020 appears to no longer be in active development. [GLPK web site here](https://www.gnu.org/software/glpk/).

## Which solver to use?

There is no simple answer to this question, but here's a few point to consider:

* If you have no budget available to purchase one of the faster commercial solvers, we suggest starting with HiGHS. Its performance is very good for a freely available tool. HIGHS is built-in to NEMO so no additional steps are required to use it once NEMO is installed.
* If you want to step up to one of the faster commercial solvers (Gurobi, CPLEX, XPress, MOSEK), please contact the manufacturers to get a price quote.  These solvers are generally much faster than the open-source options, especially for larger data sets.  They are also generally better at solving problems with a much larger range of values, which is typical for data sets that have many time slices.  The commercial solvers are generally more able to take advantage of the multi-threading capabilities of modern CPUs.  If you work at an academic agency you may qualify for low or reduced cost licenses for these solvers. Different solvers have different advantages and capabilities. At SEI we primarily use GUROBI and CPLEX for our own energy scenario modeling, but XPRESS is also very powerful.
* If you are already working with other energy modeling frameworks such as TIMES or OSeMOSYS, check to see which solvers they support.  For example TIMES/GAMS is commonly used with CPLEX.  If you have an existing CPLEX license, you may be able to utilize that with LEAP/NEMO.

## Using Different Solvers

[See this page](../18%20-%20Expressions/Yes.md) for instructions on how to use LEAP to control which solver is used by NEMO