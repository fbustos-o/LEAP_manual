---
Source: https://leap.sei.org/help24/TechSupport/Folder_Structure.htm
---

# Folder Structure

This page outlines the locations where key LEAP files are stored.  Note that this folder structure has changed in recent versions compared to LEAP2018 and earlier.

\Program Files(x86)        {for 32-bit version, or \Program Files on 64-bit Windows)  
  \LEAP                    {Contains EXEs, various zip files used to run LEAP, etc.}

\My Documents\LEAP Areas   {Contains various sub folders. Each area stored as a separate sub folder. Location can be edited via Settings: Folders}  
    \_Backup               {Zipped backups of areas - can be accessed using Area: Revert to Version option}  
    \_Settings             {Various LEAP settings}  
      \_DefaultNX          {Contains the default area used as the basis for making a new area (each instance in a separate numbered sub folder)}  
      \_DictionaryNX       {Contains the data dictionary - used as the basis for upgrading older data sets to the latest version (each instance in a separate numbered sub folder)}  
      \_Temp               {Temporary files}

      \Palettes            The color palettes used by LEAP's charts.      
      \_Pictures           {Various images used for customizing charts}  
      \Locale              {Language translation files}  
      \Webserver           {Files used for generating Sankey diagram}  
    \Freedonia             {The sample Freedonia area}  
    \...and all other areas

A folder named "_LEAPWork" is used to temporarily store area data while it is being edited.  Each running instance of LEAP stores its data in a separate numbered sub folder "0", "1", "2", etc.) underneath _LEAPWork.  The _LEAPWork folder is located under the Windows %Temp% folder (normally "C:\Users\[UserName]\AppData\Local\Temp"). This new location should be guaranteed not to be synchronized to a cloud service such as Dropbox, Google Drive, or OneDrive, and so should avoid the possibility of file locking errors caused by these services.