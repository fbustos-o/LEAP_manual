---
Source: https://leap.sei.org/help24/Concepts/LCDS__The_LEAP_Cloud_Data_Server.htm
---

# LCDS: The LEAP Cloud Data Server

## Overview

The LEAP Cloud Data Server (LCDS) is an easy-to-use, internet-hosted database containing international open-source data covering energy, emissions, and development data that can easily be accessed using LEAP.  The LCDS makes it easy to find and access much of the data you need to conduct a LEAP analysis.  

Currently, the LCDS provides national statistics useful to energy modelers including drawn from the following sources:

* [U.N. World Population Prospects](https://population.un.org/wpp/)
* [U.N. World Urbanization Prospects](https://population.un.org/wup/)
* [U.N. Energy Statistics](https://unstats.un.org/unsd/energystats/)
* [Word Bank Development Indicators](https://databank.worldbank.org/source/world-development-indicators)
* [EDGAR - Emissions Database for Global Atmospheric Research](https://edgar.jrc.ec.europa.eu/)
* [The KAPSARC Global Degree-Days Database](https://www.kapsarc.org/research/projects/global-degree-days-database/)
* [The](https://globaldatalab.org/areadata/)[Global Data Lab Area Database](https://globaldatalab.org/areadata/) (Economic and Well-Being and Development Indicators)
* [Historical GDP from World Bank data with projections based on the Shared Socioeconomic Pathways projections (SSPs)](https://en.wikipedia.org/wiki/Shared_Socioeconomic_Pathways) based on data and projections from the World Bank, IMF, OECD, and the [IPCC Sixth Assessment Report](https://www.ipcc.ch/assessment-report/ar6/) (AR6).
* [IDEES:](https://joint-research-centre.ec.europa.eu/scientific-tools-and-databases-0/potencia-policy-oriented-tool-energy-and-climate-change-impact-assessment/jrc-idees_en)[The Integrated Database of the European Energy System (JRC‑IDEES)](https://joint-research-centre.ec.europa.eu/scientific-tools-and-databases-0/potencia-policy-oriented-tool-energy-and-climate-change-impact-assessment/jrc-idees_en): A consistent set of disaggregated energy-economy-emissions data available for each Member State of the European Union.

## Using the LCDS

Data from the LCDS can easily be included in a LEAP model through LEAP's [Time-Series Wizard](https://cdn.leap.sei.org/help24/Wizards_and_Properties/Time_Series_Wizard.htm). Data is cached locally so that LEAP models drawing from the LCDS can be used even when you do not have an active internet connection. Once a LEAP model is linked to the LCDS, LEAP will regularly check with the LCDS server to see if more up-to-date data is available. If so, LEAP will alert you and offer to update your model with the new data (this capability coming soon).

The LCDS uses a simple, standard, open-source API (Application Programming Interface) based on [JSON](https://en.wikipedia.org/wiki/JSON) and [RESTFUL](https://en.wikipedia.org/wiki/REST) protocols, so that its data could also be connected to other modeling tools.  

The LCDS server and its data [can be explored directly here](https://leap.sei.org/data).