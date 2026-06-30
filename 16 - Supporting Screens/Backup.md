---
Source: https://leap.sei.org/help24/Supporting_Screens/Backup.htm
---

# Backup

Menu Option: Area:Backup

Using the Backup (![](../assets/images/NewButtons/Backup.png)) option you can copy an entire LEAP area to a single .leap file.  Backup will first prompt you to select the folder where you want to place the backup and the name of the file.  By default the file name is the same as the area name, although you can back the area up to any legal file name.  The file will always be saved with the .leap extension.  If you select a file that already exists, LEAP will ask you to confirm that you want the new backup to overwrite that file.

Once you have selected the folder and file name, LEAP will then ask you if want to also include any of the saved versions of the area within the backup.  Backup will always save the current area you are working on, and you can also choose to include one or more saved versions of the area in the backup. These versions are created automatically by LEAP or when you use the Area: **Make Version** menu option.  See the [Manage Areas](Area_Manager.md) screen for more information on how versions are automatically created by LEAP. The three options are:

* All saved versions,
* None (no versions),
* Named versions that have been saved with a specific comment.

When you restore a backed up area from the Area: **Install From File** menu option, LEAP will install the area along with any of the additional backed up versions of the area.

## Notes

* If you choose "Named", LEAP will not backup any unnamed versions that were created automatically by LEAP.
* Even if you choose **None**, you will still be backing up the current "live" version of your area.
* The .leap files created during a backup are single files containing all of the data associated with a single Area.  You can email and share .leap  files to other users of LEAP.  To install an area from a .leap file, simply double-click it in Windows or Explorer or drag and drop it onto LEAP's main screen.
* .leap files are simply standard .zip files that have been give a special file extension to make them immediately recognizable to LEAP.  Zip files are a standard format file used for archiving data. If you wish to rename a .leap file as a .zip file you can then open it in any program designed to work with .zip files. Note that the zip files have a simple password: "LEAP".