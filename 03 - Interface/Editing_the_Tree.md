---
Source: https://leap.sei.org/help24/Screen_Layout/Editing_the_Tree.htm
---

# Editing the Tree

See also: [Tree](TreeOverview.md), [Types of Tree Branches](Types_of_Tree_Branches.md), [Tree Toolbar](Tree_Toolbar.md)

The tree, which appears in the [Analysis View](../02%20-%20Views/Data_View.md), the [Results View](../02%20-%20Views/Results_Screen.md), and the [Notes View](Notes.md) is a hierarchical outline used to organize and edit the main data structures in a LEAP analysis. In most respects the tree works just like the ones in standard Windows tools such as the Windows Explorer. You can rename branches by clicking once on them and typing, and you can expand and collapse the outline by clicking on the +/- symbols to the left of each branchAn item on the tree. Different types of branches are represented by different icons on the tree icon. Note that in addition to organizing data in a hierarchical tree, you can also use [tags](../15%20-%20Tagging%20Branches/Tagging_Branches.md) to assign your data to multiple categories.

Additional options to edit the tree can be accessed in a number of ways:

* By right-clicking on the tree and selecting an option from the pop-up menu that appears,
* by using Tree menu (which contains an expanded set of options),
* by clicking on the Properties (![](../assets/images/NewButtons/Properties.png)), Add (![](../assets/images/NewButtons/Add.png)) and Delete (![](../assets/images/NewButtons/Delete.png)) buttons on the main toolbar, or
* by using short-cut keys for the most common option (e.g. Alt+P for Properties, Ctrl+Ins to add a branch, Ctrl+Del to delete a branch, etc.). Valid short-cut keys are displayed on the main menu.

A few of the most common options are worth explaining further:

![](../assets/images/NewButtons/Hide%20Branches%20in%20Tree.png) [Select Visible Branches](../16%20-%20Supporting%20Screens/Set_Region_Branches.md):  This option is used to selectively show or hide branches. In multi-region models, branches can be hidden in one or more regions.

![](../assets/images/NewButtons/Arrow-up.png) Up and ![](../assets/images/NewButtons/Arrow-down.png)Down: These buttons are used to move relative to its immediate neighbors. Use these buttons to quickly reorder branches, or alternatively you can [drag-and-drop branches](#dragndrop) as you would in Windows Explorer.

![](../assets/images/NewButtons/Properties.png) Properties (Alt+P) sets the properties of a tree branch. Different types of branches have different properties dialogs as follows:

* [Demand Branch Properties](../05%20-%20Demand/Demand_Properties_Wizard.md)
* [Key Assumptions Properties](../21.6%20-%20Wizards%20and%20Properties/Macrovariable_Properties_Wizard.md)
* [Module Properties](../08%20-%20Transformation/Module_Properties_Wiziard.md)
* [Output Fuel Properties](../08%20-%20Transformation/Output_Fuel_Wizard.md)
* [Resource Properties](../10%20-%20Resources/Resource_Properties.md)
* [Non-Energy Sector Branch Properties](../13%20-%20Non%20Energy%20Sector%20Effects/Non-Energy_Sector_Properties.md)

![](../assets/images/NewButtons/Add.png) Add (Ctrl+Ins) adds a new branch to the tree. In general new branches are added below the currently highlighted branch. However, when a "leaf" branch such as a Demand deviceA type of demand branch, which contains information about a fuel-using technology. or Transformation processA Transformation branch that describes an individual technology or group of technologies within a module such as a particular electric plant or oil refinery , another branch at the same level will be added. When adding a branch you will be asked to specify the name and properties of the new branch using dialog boxes listed above.

![](../assets/images/NewButtons/Delete.png) Delete (Ctrl+Del) is used to delete the current highlighted branch and all branches underneath it. You will be asked to confirm the operation before the branch is deleted, but bear in mind that a delete cannot be undone. Note however that you can exit LEAP without saving you data set to restore it to its status prior to the previous Save operation.

![](../assets/images/NewButtons/Delete%20X2.png) Delete All Branches Below Current Branch: Deletes all branches below the current highlighted branch.  Note that locked branches and some other types of branches cannot be deleted.

![](../assets/images/NewButtons/Cut.png) Cut Branches (Ctrl+X) is used to used to mark a branch and all branches below it to be cut. Select Paste Branches (![](../assets/images/NewButtons/Paste.png)) to move the cut branches to a new position in the tree. Notice that unlike a conventional cut operation in a standard Windows application, the cut branches operation does not actually delete or copy the branches to the Windows clipboard.

![](../assets/images/NewButtons/Copy.png) Copy Branches (Ctrl+C) is similar to the Cut operation except that on the subsequent Paste command, branches are subsequently copied not moved. Note that restrictions exist on certain operations. For example, you cannot copy or move branches between the four major categories (Key Assumptions, Demand, Transformation, and Resources) and in most cases you cannot mix branches with different icons at a single level.

![](../assets/images/NewButtons/Main%20Toolbar/open.png)[Insert Branches From](Insert_Branches_From_Folder.md) Another Area is used to insert a set of branches located in another LEAP area into the current data set at the currently highlighted branch.

* Auto-Expand specifies whether the branches in the tree automatically expand and collapse as you click on them.
* Expand All fully expands the tree.
* Collapse All fully collapses the tree.
* Outline Level expands or collapses the tree to show all branches up to the selected level of depth.

![](../assets/images/NewButtons/printer.png) Print: previews and prints the tree. Only those branches that are expanded will be printed, so you may want to right-click on the tree and select Expand All before using the print option.

![](../assets/images/NewButtons/Lock.png)/![](../assets/images/NewButtons/Unlock.png)  Lock/Unlock is used to lock or unlock a branch and optionally any branches below it. Once locked, a branch cannot be edited.

## Drag-and-Drop Editing of Branches

When editing Current Accounts data, you can move a branch (and all branches below it) by dragging and dropping it onto another branch. To copy rather than move a branch, hold down the Ctrl key and then click and drag the branches. This approach allows you to rapidly create data sets, especially those containing many similar groups of branches (for example a household sector with many similar regionally disaggregated subsectors). There are various restrictions on which branches can be dragged and where they can be dropped.