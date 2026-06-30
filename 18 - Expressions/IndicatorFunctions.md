---
Source: https://leap.sei.org/help24/Expressions/IndicatorFunctions.htm
---

# Indicator Functions

See also: [Analysis View](../02%20-%20Views/Data_View.md), [Expressions](../01%20-%20Introduction/Expressions.md)

## Summary

The [RegionIndicator](RegionIndicator.md) and [ScenarioIndicator](ScenarioIndicator.md) functions are used to compare indicators across regions and scenarios in a LEAP analysis.  LEAP supports many different kinds of comparative indicators, which are described below.

To use an indicator, pass its name or numeric value as the first parameter to the RegionIndicator and ScenarioIndicator functions.

## Supported Indicators

The supported indicators are described below:

* fMean = 0: Calculates the [arithmetic mean](http://en.wikipedia.org/wiki/Arithmetic_mean) value across the indicated regions or scenarios.  This function is particularly useful for creating your own custom comparative indicator.
* fMax = 1:  Calculates the maximum value across the indicated regions or scenarios.
* fMin = 2: Calculates the minimum value across the indicated regions or scenarios.
* fCount = 3: Counts the number of indicated regions or scenarios.
* fStdDev = 4: Calculates the [standard deviation](http://en.wikipedia.org/wiki/Standard_deviation) in values across the indicated regions or scenarios.
* fMedian = 5: Calculates the [median](http://en.wikipedia.org/wiki/Median) value across the indicated regions or scenarios.
* fGeoMean = 6: Calculates the [geometric mean](http://en.wikipedia.org/wiki/Geometric_mean) value across the indicated regions or scenarios.
* fVariance = 7: Calculates the [variance](http://en.wikipedia.org/wiki/Variance) in values across the indicated regions or scenarios.
* fVariance = 7: Calculates the [harmonic mean](http://en.wikipedia.org/wiki/Harmonic_mean) across the indicated regions or scenarios.
* fRankHigh or fRank = 9:  Ranks values from 1..n with the highest value ranked first.  Where n is the number of values.  Ranking is the simplest normalization technique. It is not affected by outliers and allows the performance of regions to be followed over time in terms of relative positions.  Performance in absolute terms however cannot be evaluated as information on levels are lost.
* fRankLow = 10:  Ranks values from 1..n with the lowest value ranked first.  Where n is the number of values.
* fPercentile = 11:  Returns the [percentile](http://en.wikipedia.org/wiki/Percentile) for a value.  The pth percentile is a value such that at most p% of the observations are less than this value and that at most (100-p)% are greater. (p is a value between 0 and 100).
* fQuartile = 12:  Returns the [quartile](http://en.wikipedia.org/wiki/Quartile) (1, 2, 3, or 4) in which the value appears when all values are  sorted into four equal parts, so that each part represents 1/4 of the sample.
* fIndexBaseYear = 13:  Calculates the ratio of the value in the current year to its value in the base year of the study.  If the base year value is itself zero, then the indicator returns a value of zero.
* fScore5 or fScore= 14:  Calculates an integer score for the indicator from1 to 5 (i.e. a five star rating).

* fScore10= 29:  Similar to fScore5 function except that it returns an integer score from1 to 10. (i.e. a marks out of ten rating )
* fZScore or fStandardization= 15: Calculates the [Z-Score or Standardization](http://en.wikipedia.org/wiki/Z-score)  of the value across the indicated regions or scenarios. Z-Scores convert values to a common scale with a mean of zero and standard deviation of one. Extreme values thus have a greater effect on the composite indicator. This might be desirable if the intention is to reward exceptional behavior.  That is, if an extremely good result for a few regions is thought to be better than a lot of  average scores. Z-Score is calculated as follows:

ZScore = (value - mean) / standard deviation

* fReScale= 16: Rescales values across the indicated regions or scenarios.

ReScale = (value - minimum) / (maximum - minimum)

* fRatiotoHigh = 17: Calculates the ratio of the value to the maximum value across the indicated regions or scenarios. If the maximum value is itself zero, then the indicator returns a value of zero.

RatioToHigh = value  / maximum

* fRatiotoLow = 18: Calculates the ratio of the value to the minimum value across the indicated regions or scenarios. If the minimum value is itself zero, then the indicator returns a value of zero.

RatioToLow = value  / minimum

* fRatiotoReference = 19: Calculates the ratio of the value to the value for a reference region. If the reference value is itself zero, then the indicator returns a value of zero.  You can choose the reference region to use for this indicator in the [General: Regions](../16%20-%20Supporting%20Screens/Regions.md) screen.  This function is not available in the [ScenarioIndicator](ScenarioIndicator.md) function.

RatioToReference = value  / reference

* fRatiotoMean = 20: Calculates the ratio of the value to the mean value across the indicated regions or scenarios. If the mean value is itself zero, then the indicator returns a value of zero.

RatioToMean = value  / mean

* fRatiotoMedian = 21: Calculates the ratio of the value to the median value across the indicated regions or scenarios. If the median value is itself zero, then the indicator returns a value of zero.

RatioToMedian = value  / median

* fDifferenceFromHigh = 22: Calculates the difference of the value from the maximum value across the indicated regions or scenarios. If the median value is itself zero, then the indicator returns a value of zero.

DifferenceFromHigh = (value  - maximum) / maximum

* fDifferenceFromLow = 23: Calculates the difference of the value from the minimum value across the indicated regions or scenarios. If the minimum value is itself zero, then the indicator returns a value of zero.

DifferenceFromLow = (value  - minimum) / minimum

* fDifferenceFromReference = 24: Calculates the difference of the value from a reference value across the indicated regions. If the reference value is itself zero, then the indicator returns a value of zero. You can choose the reference region to use for this indicator in the [General: Regions](../16%20-%20Supporting%20Screens/Regions.md) screen.  This function is not available in the [ScenarioIndicator](ScenarioIndicator.md) function.

DifferenceFromReference = (value  - reference) / reference

* fDifferenceFromMean = 25: Calculates the difference of the value from the mean value across the indicated regions or scenarios. If the mean value is itself zero, then the indicator returns a value of zero.

DifferenceFromMean = (value  - mean) / mean

* fDifferenceFromMedian = 26: Calculates the difference of the value from the median value across the indicated regions or scenarios. If the median value is itself zero, then the indicator returns a value of zero.

DifferenceFromMedian = (value  - median) / median

* fAboveBelowMean = 27:  Calculates a value of  -1, 0 or +1 depending on whether the value is below, around or above (respectively) the mean value across regions or scenarios.  Values above or below the mean are transformed such that values around the mean receive 0, whereas the ones above/or below a certain threshold receive 1, and -1 respectively.  The threshold is set to 20% of the mean.  This normalisation method is simple and not affected by outliers. However, the arbitrariness of the threshold level and the omission of absolute level information can be problematic.  The indicator is calculated as follows:

if value > mean * (1 + Threshold) then

AboveBelowMean = 1

else if value  <  mean  * (1 - Threshold) then

AboveBelowMean = -1

else

AboveBelowMean = 0

* fAboveBelowMedian = 28:  Similar to FAboveBelowMean but compares to the median value rather than the mean value.

For more information on constructing composite indicators, we recommend this paper: [Handbook on Constructing Composite Indicators: Methodology and User Guide](https://www.oecd.org/en/publications/handbook-on-constructing-composite-indicators-methodology-and-user-guide_9789264043466-en.html) (OECD, 2005)