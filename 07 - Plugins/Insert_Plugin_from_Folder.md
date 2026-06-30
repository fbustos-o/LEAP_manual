---
Source: https://leap.sei.org/help24/Plugins/Insert_Plugin_from_Folder.htm
---

# Insert Plugin from Folder

![](../assets/images/NewScreens/PluginAdd.png)

Use this screen to insert a plugin into your LEAP area. Plugins allow LEAP models to be created by quickly plugging together "mini models" of particular sectors, subsectors and industries. Plugins can be developed and maintained by subject-matter experts and will be available via an online plugin repository on the LEAP web site (coming soon).

Plugins can contain standardized methodologies including data structures, modeling relationships and default data.  When used with the LEAP Cloud Data Server (LCDS) plugins can even include data that varies by country.

To insert a plugin, first select a ".LEAPPlugin" data file.  You will then be shown the screen shown above.  The Add Plugin wizard displays information about the plugin including a description, keywords and the name of the person who created it.

Use the options on the left of the screen to connect the root branches of your plugin into your own model's branch structure.  For example, if the plugin contained a model of the household sector, you will want to insert that Household root branch immediately below your model's Demand branch.  LEAP checks the types of branches being inserted to prevent root branches being inserted in an incorrect position.

The Add Plugin wizard also includes options for handling cross cutting data such as fuels, scenarios, units etc. By default, the simple option adds all new data from the plugin into your model.  You can also choose the advanced option.  If you choose that LEAP will assist you in handling new data being added from the plugin by allowing you to add, assign or ignore individual items of data in the plugin. For example, your plugin might contain a fuel called "coal" and you might want to map (assign) that to a more specific fuel in your own model (e.g. bituminous coal).

Once a plugin has been inserted, LEAP will display a summary of what changes have been made to your area, followed by showing a set of instructions for how to use the plugin, as written by the plugin developer.  Branches added to a model from a plugin are tagged with the name of the plugin.  Immediately after plugging in, the LEAP tree is displayed with color coding to highlight which branches are associated with which plugins.