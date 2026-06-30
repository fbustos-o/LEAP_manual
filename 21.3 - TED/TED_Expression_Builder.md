---
Source: https://leap.sei.org/help24/TED/TED_Expression_Builder.htm
---

# TED Expressions

See also: [Environmental Loadings Screen](Environmental_Loadings_Screen.md), [Fuels](../16%20-%20Supporting%20Screens/Fuels.md)

You can specify environmental loadings in TEDThe Technology and Environmental Database. as either constant numeric values (e.g. X kg/ TJ of coal combusted) or you can base them on the chemical composition of the fuels being consumed or produced. This can be useful, for example, when you are entering data describing CO2 emissions from coal fired electricity generating plants. For this type of data the actual emissions will not simply depend on the quantity of coal consumed by the plant, but will also depend on the carbon content of the coal. TED allows you to enter an emission factor that accounts for this effectA pollutant emission or some other direct environmental impact from the consumption or production of energy . The actual calculated emission loading and the values calculated in your LEAP scenarios, should you choose to link LEAP to this TED technology, will then properly reflect the carbon content of the type of coal used in your local areaThe energy system being studied . FuelSomething combusted, or otherwise used to produce energy compositions are edited on the Fuels screen ([Main Menu](../03%20-%20Interface/Menu.md): General: [Fuels](../16%20-%20Supporting%20Screens/Fuels.md))

To enter this type of emission factor, you need to specify a loading using a mathematical expressionA mathematical formula used to specify how the values of a variable changes from year to year. that references the chemical composition of the fuel. In this case the expression would be:

Loading (kg CO2 / kg of fuel consumed) = CarbonContent * FractionOxidized * (CO2/ C)

The CarbonContent and FractionOxidized terms are values stored in the LEAP fuels database, while the CO2 and C terms are constants. The advantage of this approach is twofold. Firstly, environmental loadings specified in this manner are automatically updated whenever the LEAP fuels database is updated - without the need to edit the data in TED. Secondly, one default set of effects is more generally applicable, even in different regions in where fuel compositions are markedly different.

Use TED's [Expression Builder](TED_Exp_Builder.md) screen to help specify these expressions.