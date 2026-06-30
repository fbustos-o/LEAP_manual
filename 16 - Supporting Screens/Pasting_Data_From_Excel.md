---
Source: https://leap.sei.org/help24/Supporting_Screens/Pasting_Data_From_Excel.htm
---

# Pasting Data from Excel

When working in LEAP's [Analysis View,](../02%20-%20Views/Data_View.md) you can cut (Ctrl-X) or copy (Ctrl-C) data from Excel and then paste it into LEAP's expressions using the Edit:Paste (Ctrl-V) or Edit: Paste Special menu options.

If you are copying a set of data from Excel that forms a time-series (i.e pairs of years and corresponding values) then LEAP will automatically convert that data into one of its time-series expressions such as those using an Interp or Step function.  For more information, see [Pasting Arrays of Numbers](Pasting_Arrays_of_Numbers.md).

If you are pasting results from a single Excel cell then you can paste that data into LEAP as a single value using the Edit Paste menu option or (Ctrl-V) keyboard shortcut.  If the Excel cell contains a numeric value or an Excel formula that itself calculate a simple numeric value, then the LEAP expression will simply be the displayed value (as formatted on screen in Excel).  For example: if you copied cell A2 which has a formula "=2+A1" and cell A1 itself has a value of 3, then the result both for cell A2 and for the LEAP expression will be 5.  Note that LEAP will get the value of the cell as displayed on screen in LEAP, so if the Excel cell has a formula =1/3  = 0.3333 recurring, but the cell is set to show only 2 decimal places, then LEAP's expression will simply be 0.33.

In addition to pasting values copied from Excel, you can also paste a link to the values in Excel.  To paste a link to Excel use the Edit: Paste Link menu option or use the Ctrl-Alt-V keyboard shortcut.  These links will appear as expressions of the for Excel(FileName, RangeName).  Refer to the [Excel function](../18%20-%20Expressions/Excel.md) in the Expression reference for more information on this function.  Note that you can only create or paste these Excel link functions if the Excel spreadsheet has previously been saved.

When creating these link functions, if the Excel cell contains a numeric value or an Excel formula that itself calculate a simple numeric value, then the LEAP expression will return the value of the Excel cell.  Note that unlike when pasting a value from Excel, pasting a link to a cell will return the value of the cell with its full accuracy (i.e not limited by the cell formatting in Excel).  If the Excel cell itself contains a LEAP expression (e.g. an Interp or Growth function) that expression will be interpreted within LEAP as though it were entered directly in the cell where the Excel function is placed.