---
Source: https://leap.sei.org/help24/Resources/Resource_Costs.htm
---

# Resource Costs

See also: [Resource Analysis](Resource_Data.md)

All resource costs are specified using variables found under the Resource branch in the main tree data structure.

LEAP allows you to specify the indigenous production and import costs of supplying fuels as well as the benefits of exported fuels. In principle, economic theory suggests that shadow costs reflecting the full social costs, not the market costs, should be used in specifying resource costs, since LEAP's perspective is a social cost analysis. In practice, market prices may be used since these are often the only type of cost data available. In cases where the resource has no market price (e.g., traditional wood fuel collection) a proxy can be used such as the cost of substitute fuels or of sustainable forestry.

* Indigenous Production Costs: Costing indigenous resources is more subtle since the data you provide will depend on a) whether you have included mining and extraction industries as modules in the Transformation module, and b) the costing boundary used for your analysis. You can set the boundary to be used for your cost analysis in the  General: [Settings](../16%20-%20Supporting%20Screens/Basic_Parameters_Screen.md) screen. Assuming you have defined these modules and your cost boundary is drawn around the entire system, then you should enter capital and operating and maintenance (O&M) costs for the extraction modules in your Transformation analysis, and enter  "resource depletion costs" for each indigenous resource. If you are using a more restricted costing boundary, then you will need to enter the delivered cost of the fuels produced by the extraction industries. In its cost-benefit calculations, LEAP will use these delivered costs and ignore the capital and O&M costs of the extraction modules.
* Import and Export Costs: Generally the costs of imports and exports are identified directly with market prices. For imports, the CIF (cost, insurance and freight) costs would apply, and for exports, the FOB (free on board) costs would apply.
* Cost of Unmet Requirements: In addition to specifying supply costs and benefits (production, imports and exports), LEAP also allows you to specify the economic costs of not supplying energy using the variable Cost of Unmet Requirements.  This cost is essentially a measure of the economic damage done by blackouts, brownouts or other incidents of unserved demands.   Leave these values as zeros if you do not wish to quantify the costs of unserved demands.