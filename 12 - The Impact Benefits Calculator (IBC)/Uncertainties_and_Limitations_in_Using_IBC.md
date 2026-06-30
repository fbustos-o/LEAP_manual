---
Source: https://leap.sei.org/help24/IBC/Uncertainties_and_Limitations_in_Using_IBC.htm
---

# Uncertainties and limitations of IBC module

See also: [Introduction
to IBC](Introduction_to_IBC.md), [Using IBC](Using_IBC.md)

Here are notes on some key uncertainties and limitations when using
IBC within LEAP.

1. GEOS-Chem
   Adjoint coefficients for PM2.5:
   The GEOS-Chem Adjoint coefficients quantify the sensitivity of PM2.5
   concentrations in the target country to NOx, SO2,
   NH3, BC and OC emissions in grid squares across the world.
   These sensitivities are calculated for a base set of emissions, for
   the year 2010. The coefficients are applied in IBC to look at changes
   in PM2.5 concentrations in the target country that result from changes
   in emissions in the target country, and across the world. They are
   linear coefficients, which means that a change in emissions results
   in a linear increase/decrease in PM2.5 concentrations in the target
   country. The methodology therefore does not account for non-linear
   changes in target PM2.5 concentrations resulting from non-linear chemical
   reactions in the atmosphere, e.g. combination between NOx,
   SO2 and NH3 to form secondary inorganic aerosol.
2. GEOS-Chem
   Adjoint coefficients for Ozone:
   The GEOS-Chem Adjoint coefficients quantify the sensitivity of ozone
   concentrations in the target country to NOx, VOC, CO and
   CH4 emissions in grid squares across the world. These sensitivities
   are calculated for a base set of emissions, for the year 2010. The
   coefficients are applied in IBC to look at changes in ozone concentrations
   in the target country that result from changes in emissions in the
   target country, and across the world. They are linear coefficients,
   which means that a change in emissions results in a linear increase/decrease
   in ozone concentrations in the target country. Ozone formation depends
   on the relative emissions of VOC and NOx, with ozone increasing
   due with increasing NOx emissions in VOC-limited regimes,
   and with increasing VOC emissions in NOx-limited regimes.
   Hence changes in the relative emissions of NOx and VOCs
   will result in non-linear changes in ozone concentrations. This interaction
   is not taken into account in the application of the ozone coefficients
   in IBC.
3. Health
   impact assessment methodology:
   The health impact assessment estimate premature mortality associated
   with PM2.5 and ozone exposures, using concentration-response
   functions that have been used by the Global Burden of Disease project.
   These concentration-response functions are based on health effects
   research that has been carried out in North America and Europe. It
   is assumed that the same relationships apply in other regions of the
   world, including those where PM2.5 and ozone concentrations
   are much higher, and where the composition of PM2.5 may
   differ.
4. Crop
   impact assessment methodology:
   Agricultural crop yield loss is estimated using concentration-response
   functions that quantify the relationship between wheat, maize, rice
   or soy yield and ozone exposure. These functions are based on experiments  carried out in North America,
   that assessed this relationship for ozone exposure between 20 and
   90 ppb. The relationship between yield loss and ozone exposures above
   90 ppb is uncertain. To avoid unrealistic estimates of ozone-induced
   yield loss, for ozone concentrations above 90 ppb, there is assumed
   to be no increase in yield loss. This means that for mitigation scenarios
   to show a benefit for ozone crop yield loss, ozone concentrations
   must be reduced to below 90 ppb, e.g. a reduction from 110 ppb to
   100 ppb in ozone exposure does not result in an estimated reduction
   in yield loss.
5. Other: Significant but hard to quantity uncertainties
   exist in the activity levels, energy intensities and emission factors
   used in any LEAP area.  Currently LEAP's calculations are deterministic
   and do not reflect any uncertainty in these values.  However,
   you can use LEAP to perform sensitivity analyses or even connect it
   with tools such as [Oracle
   Crystal Ball](http://www.oracle.com/us/products/applications/crystalball/overview/index.html) that allow uncertainties to be explored using techniques
   such as [Monte Carlo](https://en.wikipedia.org/wiki/Monte_Carlo_method)
   analysis.  Bear in mind also that all future values are inherently
   uncertain since they depend on policy choices that may or may not
   be made.