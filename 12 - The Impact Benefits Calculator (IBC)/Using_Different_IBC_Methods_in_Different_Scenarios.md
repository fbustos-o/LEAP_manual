---
Source: https://leap.sei.org/help24/IBC/Using_Different_IBC_Methods_in_Different_Scenarios.htm
---

# Using Different IBC Methods in Different Scenarios

See also: [Introduction to IBC](Introduction_to_IBC.md), [Uncertainties and Limitations in Using IBC](Uncertainties_and_Limitations_in_Using_IBC.md), [Using IBC](Using_IBC.md)

Use the [IBC tab](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#IBCSettings) of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen to set default methods for (1) calculating health impacts as a function of exposure and (2) setting the approach used for scaling base year particulate matter emissions.

If you want to compare the results due to these different methods you can create additional scenarios in which you vary these methods.  Do this as follows:

### Health Impact Relative Risk Function

To control which function is used, create the following Key Assumption Branch: Key\IBC Settings\Relative Risk Version. Note that "IBC Settings" is itself a category branch.  Within that branch, specify an integer version number to control which function should be used.  The value can vary by scenario. The currently supported values are:

0: Global Burden of Disease 2010

1: Global Burden of Disease 2015

2: Global Burden of Disease 2019.

If the above branch is not defined or if you specify any value outside the supported range of values then LEAP will use the default method specified on the IBC tab of the Settings screen. More information on [IHME's Global Burden of Disease study here](https://www.healthdata.org/research-analysis/gbd).

### Base Year Particulate Matter Scaling

To control which approach is used, create the following Key Assumption Branch: Key\IBC Settings\PM Scaling. Within that branch specify an integer version number to control which approach should be used.  The currently supported values are:

0: No Scaling  
Base year and future concentrations calculated directly from base year LEAP emissions. Supports any base year. Can also be used if LEAP model contains only a partial accounting for relevant national particulate-forming emissions.

1: Scaling using the approach described in [van Donkelaar, 2016](https://pubs.acs.org/doi/abs/10.1021/acs.est.5b05833).

Notes: Base year concentrations are based on satellite-based estimates. LEAP emissions are only used to calculate future changes in concentrations. This second method requires LEAP base year to be set to 2010.  It also requires complete accounting for all relevant particulate-forming national emissions.

### Rest of World Emission Scenarios (ECLIPSE)

To control which background Rest of World emissions scenarios are used, create the following Key Assumption Branch: Key\IBC Settings\ECLIPSE. Within that branch specify an integer version number to control which version of the IIASA ECLIPSE scenarios should be used.  The currently supported values are either 5 or 6. [More information on the IIASA ECLIPSE scenarios here](https://iiasa.ac.at/models-tools-data/global-emission-fields-of-air-pollutants-and-ghgs).

If any of the above IBC Settings branches are not defined (or if you specify values outside the supported range) then LEAP will use the default values specified on the IBC tab of the [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md#IBC) screen.