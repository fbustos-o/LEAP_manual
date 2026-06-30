---
Source: https://leap.sei.org/help24/Demand/Environmental_Analysis.htm
---

# Environmental Loadings

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Demand Analysis](Demand.md), [Transformation Analysis](../08%20-%20Transformation/Transformation.md), [TED: The Technology and Environmental Database](../21.3%20-%20TED/TED_Intro.md)

All devices in your Demand analysis, and all feedstock fuels, auxiliary fuels and output fuels in your Transformation analysis are potential sources of environmental loadings. Use the environmental loadings screen to associate environmental loadings with these branches. Each loading is specified as an [effect](../16%20-%20Supporting%20Screens/Effects_Screen.md) (e.g. a pollutant emission) per unit of energy consumed or energy produced or per unit of vehicle distance (this latter approach is only available when conducting a Demand [Transport Analysis](Transport_Analysis.md)). During its calculations, LEAP multiplies the loadings you specify on the Environmental loadings screens by the total amount of energy consumed in each year of each scenario. In the case of distance-based loadings, LEAP multiplies the loadings by the total mileage of all vehicles.

## Linking to TED

The simplest way to specify environmental loadings for a given technology is to create a link to one of the library of technologies in the accompanying [Technology and Environmental Database](../21.3%20-%20TED/TED_Intro.md) (TED). TED contains emission factors for hundreds of energy consuming and energy producing technologies, including the default emission factors suggested by the IPCC for use in climate change mitigation analyses. To create a link to TED, click on the double-plus button (![](../assets/images/NewButtons/AddX2.png)) and use the subsequent dialog box (shown right) to select a technology from TED that closely matches the technology in your Area.

![](../assets/images/NewScreens/TEDLink.png)

Notice that you are not required to specify loadings for all fuels, and in fact you will not normally wish to specify loadings for Demand devices consume heat or electricity since the emissions for those fuels occur upstream (e.g., during the generation of electricity) from the point of consumption and can be modeled in LEAP's Transformation calculations. However, you should note that the default emission factors in TED are all direct emission factors, not lifecycle emission factors. For example, the emission factors for a vehicle are the direct emissions from the vehicle: they do not include the upstream emissions from oil refining and oil extraction. You should also be aware that while TED is based on a literature review of recently published estimates of emission loadings; it does not currently contain a comprehensive picture of all effects from each of its source categories. For this reason, be sure to examine which effectA pollutant emission or some other direct environmental impact from the consumption or production of energy categories are included for each TED technology.

## Entering Emission Factors Directly

The latest version of LEAP now allows you to manually enter your own emission factors, or override the default factors obtained by linking to TED. So for example, you might link to the IPCC factors for greenhouse gases, but then add your own country- or technology-specific factors for other air pollutants. As with other LEAP expressions, emissions factors can be specified as simple numbers or as mathematical formulae. In fact, many of the emission factors stored in TED are expressed as formulae in which the emission factor is itself a function of the chemical composition of the fuel being burnt. For example, SO2 emission factors are generally a function of the sulfur content of the fuel, and CO2 emission factors are often expressed as a function of the carbon content of the fuel. For more information on specifying environmental loadings, refer to information on the [TED expressions](../21.3%20-%20TED/TED_Expression_Builder.md).

To add an emission factor, click the ![](../assets/images/NewButtons/Add.png) button and select from the list of available effects. You can add additional effects on the [Effects](../16%20-%20Supporting%20Screens/Effects_Screen.md) screen. Any environmental loadings created as links to TED are initially protected in Current Accounts and cannot be changed except by editing the data in [TED](../21.3%20-%20TED/TED_Intro.md) itself.  Click the ![](../assets/images/NewButtons/Delete.png) button to delete an effect. Environmental loadings are also shown as branches on the tree in [Analysis View](../02%20-%20Views/Data_View.md) marked with the cloud icon (![](../assets/images/NewButtons/effects.png)), and can also be deleted directly be editing the tree. When editing scenarios, future values for environmental loadings can always be edited, even for those loadings linked to TED.

## Units

For unlinked loading factors, you can edit the numerator and denominator units for each factor in Current Accounts. The choice of numerator units will depend on the effect being specified, while the choice of denominator units will depend on the state of the fuel being consumed or produced, and also on the type of loading factor. Most loading factors are specified per unit of energy consumed. However, you can also specify emissions per unit of energy produced for any output fuel. In addition, when conducting Dema
nd [Transport Analyses](Transport_Analysis.md), you can also specify emission per unit of vehicle-distance traveled (e.g. grammes per vehicle-mile). This reflects how most pollutants are regulated for vehicles and thus how these factors are best modeled.

### 

## Dynamic Emission Factors

As with other LEAP expressions, in scenarios you can specify how environmental loading factors are likely to change in the future. By default, the factors you specify in scenarios describe the average emission factors for the total stock of devices producing the loading. However, when conducting [Stock Analyses](Stock_Analysis.md) and [Transport Analyses](Transport_Analysis.md) in Demand
the 
environmental loading factors will instead be interpreted as values for newly added technologies. In these cases, LEAP will internally calculate the stock-average environmental loading factors.

In addition, when conducting [Stock Analyses](Stock_Analysis.md) and [Transport Analyses](Transport_Analysis.md) in Demand, you can now specify
an optional [lifecycle profile](../16%20-%20Supporting%20Screens/LifeCycle_Profiles.md) 
that describes for each vintage, how emission factors degrade as technologies age.