---
Source: https://leap.sei.org/help24/Supporting_Screens/Time_Slices.htm
---

# Time Slices

Menu Option: General:Time Slices  
See Also: [Yearly Shapes](Load_Shapes.md)

## The Time Slices Screen

![](../assets/images/NewScreens/TimeSlices.png)

Time slices are the seasonal and time-of-day divisions into which annual energy demands can be divided.  Time slices allow you to look in detail at how energy demands and supplies vary compared with the annual calculations used elsewhere in LEAP.  For example, electric device loads might vary both by season (summer, winter, spring and autumn) and by time of day (week day, week night, weekend day, weekend night).

## Setting Up Time Slices

Time slices can be created manually using the add and delete buttons, but in most cases we suggest you use the Setup button (![](../assets/images/NewButtons/document-white.png)) accessed from the tool bar to create the time slices for your analysis.  Bear in mind that each area can only have one set of time slices.  Other supporting information such as the [yearly shapes](Load_Shapes.md) used to define variations in demand and supply must all be specified for the same set of time slices.

![](../assets/images/NewScreens/TimeSlicesSetup1.png)

Calculations in LEAP assume that every year has the same time slices.  LEAP assumes that every year has 8760 hours and there are no leap years (ironically!).  Every year begins on a Monday.

## Simple and Detailed Time Slices

When using the Setup wizard, you can either choose a simple approach in which a year is divided into a set number of slices of a certain duration, or a more detailed approach in which slices are based on seasonal or monthly groups, weekday/weekend groups and time of day groups.  The simple approach is most useful where you only want to specify a load duration curve but do not have information about seasonal or daily/hourly variations in demand and supply. The detailed approach gives you a wide array of choices for setting up time slices as shown below.

![](../assets/images/NewScreens/TimeSlicesSetup2.png)

You can choose to create seasonal, quarterly, monthly, weekly, or even daily time slices.  Slices may also reflect the differences between weekdays and weekends or between daylight and night time hours. The total hours across all time slices must sum to the number of hours in a nominal year (8760 hours).  You can adjust the definitions of groupings (e.g. the start/end date of seasons, the days in weekdays and weekends, or the hours in days & nights via the [time slice settings](Time_Slice_Settings.md) screen, available from the tool bar in the Time Slice screen.

Some configurations of seasons, days and hours lead to a large number of time slices.  LEAP will warn you in situations where the number of time slices are very large as this will lead to high memory use and slow calculations.  Some configurations may lead to out of memory errors if using the 32-bit version of LEAP.  In these cases, we recommend you use the 64-bit version which is able to take full advantage of the memory available on modern PCs.

Once you have chosen the desired time slicing configuration in the Setup screen, select OK and LEAP will generate a complete set of time slice data and display these to you for review and further editing in the time slice screen.  The data displayed summarizes the names and groupings of each slice and the duration of each slice in hours.  Notice that the sum of the hours across all slices should equal the total number of hours in the year (8760 hours).  You can use data editing features in the time slice screen to manually edit the data for each slice but this is not normally recommended.  These features include the ability to import and export data to Excel and to add, delete and reorder individual time slices.  You can also filter the slices displayed in the screen to display only a subset of slices for easier editing.

LEAP also provides choices about how to model seasonal and time of day variations in loads.   The simplest approach is to specify the overall load shape exogenously for the whole system.  A second approach is to specify the shape of the load of each individual device consuming electricity (in your demand analysis) in which case LEAP will endogenously calculate the overall system load shape by summing across all of the individual device loads.  To choose between these different approaches, go to the Calculations tab of the General: [Settings](Basic_Parameters_Screen.md#Loads) screen and choose a setting for Load Shapes.  In both cases, load shapes are specified by entering data for each time slice in the General: [Yearly Shapes](Load_Shapes.md) screen. You can create a library of different load shapes in this screen (for example, you might create one shape for lighting, another for industrial loads and others for refrigeration and hot water heating)   Yearly shape data can be specified either as a fraction of the annual peak load (% of peak) or as a fraction of the annual energy load (% of energy).  Note that when using LEAP's optimization calculations, load shapes must currently be specified as a fraction of the annual energy load (% of energy).

* When specifying an overall load shape exogenously for the whole system, go to the relevant Transformation module in LEAP's tree and in the Current Accounts scenario specify the yearly shape in the System Peak Load Shape variable (if using the % of peak method) or in the System Energy Load Shape variable (if using the % of energy method).  Note: these variables are only visible when editing the Current Accounts scenario.  In both cases, the load shape can be entered using the [YearlyShape](../18%20-%20Expressions/YearlyShape.md) function.  So for example, if you want to tell LEAP to use the load shape named "System Load Shape" you would enter the following expression:  YearlyShape(System Load Shape.
* When specifying shapes for individual demand devices, go to the [Load Shape](../05%20-%20Demand/Load_Shape.md) variable, which is available for each individual demand technology (![](../assets/images/NewButtons/Tech%20Gray.png)) when editing the Current Accounts scenario.  As noted above, load shapes can most easily be specified using the [YearlyShape](../18%20-%20Expressions/YearlyShape.md) function.  So for example, if you want to tell LEAP to use the load shape named "Lighting" you would enter the following expression: YearlyShape(Lighting).