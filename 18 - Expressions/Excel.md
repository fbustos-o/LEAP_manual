---
Source: https://leap.sei.org/help24/Expressions/Excel.htm
---

# Excel

## Syntax

Excel(FileName, RangeName)

## Summary

This function creates a permanent link to a value entered in an Excel spreadsheet cell.  Once you create this type of expression, the values in LEAP will be updated whenever the Excel spreadsheet is changed and then saved.

Note that you can only create or paste these Excel functions if the Excel spreadsheet has previously been saved.  That is, you cannot create links to in-memory only spreadsheets.

When LEAP evaluates these functions, if the Excel cell contains a numeric value or an Excel formula that itself calculates a simple numeric value, then the LEAP expression will return the value of the Excel cell.  Note that unlike when pasting a value from Excel, pasting a link to a cell will return the value of the cell with its full accuracy (i.e. not limited by the cell formatting in Excel).

If the Excel cell itself contains a LEAP expression (e.g. an Interp or Growth function) that expression will be interpreted within LEAP as though it were entered directly in the cell where the Excel function is placed.

Please also refer to the [Interp](Interp.md) and other time series functions, which can similarly be specified to include references to Excel spreadsheets.

Tip: The easiest way to create Excel expressions is to use the Edit: Paste Link menu option (Ctrl-Alt-V) to paste a cell previously copied in Excel