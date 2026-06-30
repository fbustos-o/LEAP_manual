---
Source: https://leap.sei.org/help24/Supporting_Screens/Pasting_Arrays_of_Numbers.htm
---

# Pasting Arrays of Numbers into LEAP

![](../assets/images/NewScreens/ArrayPasteOptions.png)When working in LEAP's [Analysis View,](../02%20-%20Views/Data_View.md) you can cut or copy arrays of numbers (e.g. from Excel) and then paste them into LEAP.  LEAP will automatically detect when you are trying to paste more than one value and will use that array of values to construct a time series function [(Interp](../18%20-%20Expressions/Interp.md), [Step](../18%20-%20Expressions/Step.md), [LinForecast](../18%20-%20Expressions/LinForecast.md), etc.).

In addition to handling individual values, LEAP will also automatically handle the following situations:

* Two rows of data with the first row containing years and the second row containing values.  The years should be in ascending chronological order but need not be evenly spaced (so for example, the series 2000, 2003, 2005, 2010 would be acceptable but, 2000, 2005, 2002 would not be acceptable).
* Two columns of data with the first column containing years and the second column containing values.
* One row of data.  The row is assumed to contain yearly values, sorted from left to right in ascending chronological order.  The first time you paste this type of information LEAP will show the dialog box shown here, which will ask you for the year corresponding to the first value and the time interval in years between the values.  It will also ask you for the type of function to be pasted  [(Interp](../18%20-%20Expressions/Interp.md), [Step](../18%20-%20Expressions/Step.md), [LinForecast](../18%20-%20Expressions/LinForecast.md), etc.). The settings you choose will be used for subsequent paste operations.  In this way, you can quickly copy and paste multiple blocks of text.  Use the "Paste Special" option to force LEAP to show the dialog again to change the paste options.
* One column of data.  The column is assumed to contain yearly values sorted from top to bottom in ascending chronological order. See notes above on data in one row.