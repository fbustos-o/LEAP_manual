---
Source: https://leap.sei.org/help24/API/Using_the_Script_Editor.htm
---

# Script Editor

Menu option: Advanced: Edit Scripts   
See also: [Automating LEAP with the API](API.md)

![](../assets/images/NewScreens/ScriptEditor.png)

## Overview

The script editor is used to edit, interactively debug and run scripts that automate LEAP and connect it with other Windows programs using standard  [COM Automation](https://msdn.microsoft.com/en-us/library/windows/desktop/ms221375(v%3dvs.85).aspx) programming techniques.  The script editor uses Microsoft's Windows Script technology.  More information on [Windows Script](http://msdn2.microsoft.com/en-us/library/ms950396) is available here.

The script editor supports multiple windows scripting (programming) languages. In addition to BASIC (VBScript) - the default language - which uses files with extension .vbs, .vbe, .vb and .bas, the script editor also supports JScript (.js or .jscript), Python (.pys) and Perl (.pls) files.  The styling features of the script editor automatically adjust to support each of these languages once a scripting file is opened or created.  The language is detected automatically when you open one of these files based on its extension.  The active scripting language is displayed in the caption of the script editor.

## Using the Script Editor

The script editor is divided into three panes.

* At the top left is the edit pane where you edit your scripts.  Use the Open (![](../assets/images/NewButtons/open.png))button to open a script to be edited. You can open scripts stored in the current area folder or in the common "_SCRIPTS" folder.  Use the **S**ave (![](../assets/images/NewButtons/save.png))or Save As (![](../assets/images/NewButtons/SaveAs.png)) buttons to save the script.  Use the New (![](../assets/images/NewButtons/document-white.png)) button to delete the current script.  The editor also supports standard editing options such as cut (![](../assets/images/NewButtons/Cut.png)), copy (![](../assets/images/NewButtons/Copy.png)), paste (![](../assets/images/NewButtons/Paste.png)), undo (![](../assets/images/NewButtons/Undo.png)),  and find (![](../assets/images/NewButtons/find.png)).  Use the Run Script button (![](../assets/images/NewButtons/Play.png)) or press Ctrl-Enter to run the script.  The script editor supports integrated debugging. Syntax or run-time errors in the script will cause the script to stop running.  The type of error, and the line and column at which it occurred will be reported, and the edit cursor will be placed at the place in the script where the error occurred, helping you to fix the problem.
* At the bottom of the window is a PRINT output pane.  Any PRINT messages will appear here.  You can clear this pane using the **c**lear button (![](../assets/images/NewButtons/Delete%20V2.png)) on the right of the pane or by issuing a LEAP.CLS command in your script.
* On the right of the window is a pane with two tabs.  These tabs give access to [LEAP API objects](API.md) and to LEAP Branch and variable names, which you may want to include in your scripts.  Select an object in the tree and then click the Add button (![](../assets/images/NewButtons/Arrow-left.png)) to add it to the edit pane on the left.   At the bottom of the pane you can see detailed help information for each enumerated object including help information describing each object, whether an object is a method or a property, the type of the return object, and whether it is read-only or is read/write (can be edited).  Note that some of the less-used objects in the API may be specified as read/write but trying to set their values will return a "not implemented yet" error.    
    
  Note also that in addition to referring to LEAP objects you can also create references to many other COM objects.  Many Windows based programs support COM, allowing you to connect LEAP to other programs such as Excel, Word, PowerPoint, etc.

The Script Editor includes an auto-complete feature that helps you to include references to LEAP API objects in your scripts.  When typing a period after an object, LEAP pops up a dialog box showing all of that object's properties and methods. The popup box includes documentation for each method including the list and type of any required parameters. LEAP can deduce the type of a variable assigned to LEAP objects enabling code completion to work in most situations.