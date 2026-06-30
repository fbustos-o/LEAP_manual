---
Source: https://leap.sei.org/help24/Screen_Layout/Version_Control.htm
---

# Version Control

See also: [Manage Areas](../16%20-%20Supporting%20Screens/Area_Manager.md), [Backup](../16%20-%20Supporting%20Screens/Backup.md)

## Introduction

LEAP allows you to create multiple versions of your areas as a way of saving important milestones in your research. For example, once you have finished entering the Current Accounts for an area, you might create a version with the comment "Current Accounts complete."  As another example, suppose you had just finished a study and written a paper, you might create a milestone version, with the comment "Finished paper."  As another example of the use of versions, this capability is also used within the sample Freedonia data set as a way of storing different versions of the area that correspond to different points in the LEAP training exercises.

## Using Version Control

Versions of areas are automatically created when an area is saved. Versions are placed in the _backup folder with the area name and the backup date and time. For example, a version of Freedonia from 2.30 PM on March 2, 2025 would be named Freedonia_2025_3_2_14_30.zip.

As versions accumulate, LEAP will selectively and automatically remove some of the saved versions: balancing the need to keep previous versions with the need to preserve disk space. Several versions will be preserved from the previous 24 hours, plus one per day for the last seven days, one per week for the last month, one per month for the last year, and one per year before that.  In addition LEAP will automatically save a named version whenever LEAP upgrades an area from one dictionary version to another. This occurs when upgrading to new versions of LEAP.

You can also create your own **named** versions of areas, using the Area: **Make Version** menu option (![](../assets/images/NewButtons/date-move-back-one-day.png)) and giving it an optional comment. Named versions are especially important for recording milestones in a project. LEAP will never automatically delete named versions of your areas (ones with a comment).  However, you can manually delete versions from within the Area: [Manage Areas](../16%20-%20Supporting%20Screens/Area_Manager.md)menu option (![](../assets/images/NewButtons/LEAP-Area.png)).

You can use the Area: **Revert to Version** menu option (![](../assets/images/NewButtons/date-add-2.png)) to revert an area to one of the saved versions. When you do this the version will overwrite the currenmt working copy of your area.  This capability allows you to go back to a previous version of your area.

## Versions and Backup

When you backup an area using the Backup option on the main toolbar (![](../assets/images/NewButtons/Backup.png)), LEAP will create a copy of your area in a single .leap file.  When creating a backup, LEAP will ask you if want to also include any of the saved versions of the area within the backup.  Backup will always save the current version of the area you are working on, and you can also choose to include one or more saved versions of the area in the backup. The three options are:

* **All**saved versions,
* None (no versions),
* Named versions that have been saved with a specific comment.

When you restore a backed up area from the Area: **Install From File** menu option, LEAP will install the area along with any of the additional backed up versions of the area.

##