---
title: [SpotIQ Algorithms]
summary: "SpotIQ has a variety of algorithms for outlier detection, trend analysis, cross-correlation analysis, comparative (diff) analysis, explain (classification) analysis, K-mean clustering, time series forecasting, and binomial logistic regression."
last_updated: 12/12/2019
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

{: id="outlier-detection"}
## Outlier detection

ThoughtSpot uses several different algorithms to detect outlier data:

{: id="z-scores"}
### Z-Scores

Z-Scores algorithm calculates the number of standard deviations between the data point and the mean value of the reference population, in number of standard deviations.

The basic Z-Score formula is:

```
z = (x – μ) / σ
```

{: id="median-z-scores"}
###  Median Z-Scores

Similar to [Z-Scores](#z-scores), Median Z-Scores measures outlier strength. It calculates ratio of the difference from the median and the median absolute deviation (MAD).

{: id="s-h-esd"}
### Seasonal Hybrid Extreme Studentized Deviate

This technique detects outliers in seasonal univariate time series. You can use this algorithm to detect both global and local anomalies by employing time series decomposition and robust statistical metrics. For long time series (6 months of minute data, for example), the algorithm uses piecewise approximation for anomaly detection.

{: id="linear-regression"}
### Linear Regression

The least squares method determines the best fit line for time series data. SpotIQ considers any value outside `ℓ +/- N * σ` an anomaly, where `ℓ` is the linear model fit into the data, and `σ` is the standard deviation.

{: id="time-series"}
### Time Series

We use the R package `tsoutliers` that implements a procedure based on the approach described in [Chen and Liu (1993)](https://www.istat.it/it/files/2014/06/Joint-Estimation-of-Model-Parameters-and-Outlier-Effects-in-Time-Series.pdf) to automatically detect outliers in time series. This algorithm considers innovational outliers, additive outliers, level shifts, temporary changes, and seasonal level shifts.

It is available as an R template.


{: id="trend-analysis"}
## Trend analysis

In this algorithm, we use the least squares method to determine the best fit line for time series data. The algorithm selects the most noticeable positive and negative trends based on the tightest confidence interval and the most extreme positive or negatives slope, and automatically displays this trend along with the best fit line.

{: id="cross-correlation-analysis"}
## Cross-correlation analysis

SpotIQ uses cross correlations to determine relationships between measures on shared time dimensions for leading or lagging indicators.

It creates two independent time series data sets, and iterates through a range of time shifts to find the greatest correlation (highest correlation coefficient). The result of a cross-correlation analysis shows how strong the relationship between two data sets is, and in what direction it is developing over time. The range is -1 to 1. Results closest to 1 show the strongest correlation.

{: id="comperative-analysis"}
## Comparative analysis

Also known as _diff_ analysis, this algorithm aims to explain the differences between two selected data points in a given metric, sliced by other attributes. As a result, we can see to what degree this new attribute can explain the differences between the two points.

See [Comparative analysis]({{ site.baseurl }}/spotiq/comparative-analysis.html)

{: id="explain-analysis"}
## Explain analysis

Also known  as _classification_ analysis, this algorithm explains the bucketing (or classification) of data into categories.

More specifically, _anomaly_ explanation analysis explains the outlier points in an anomaly insight by ranking the measures and attributes that contribute the most into partitioning the data into the categories: anomaly vs non-anomaly. A user can also select the points on a chart and invoke this analysis that discriminates the selected points from the unselected ones or have the categories specified by a classification column in the table or worksheet and choose Classification as the algorithm under the Advanced tab of SpotIQ Analyze dialog.

To use Explain or Classification analysis, the query or table must have at least one grouping column. In case of multiple attributes and measures, the algorithm picks the first measure and the first attribute for the explanation/classification.

This algorithm uses random forest (RF) algorithm for measures, and mutual information (MI) analysis for attributes. RF creates a decision-tree based model that predicts the value of a target variable based on several input variables that are related measures. MI analyzes mutual information between related attributes and the target variable. The objective is to determine how much information content we can learn about the target variable (buckets), given each related attribute.

{% include note.html content="This algorithm is not on by default. Work with your Customer Success team to enable Explain or Classification analysis." %}

{: id="k-means-clustering"}
##  K-means clustering

K-means clustering partitions `n` observations into `k` clusters, where each observation belongs to the cluster with the nearest mean, serving as a prototype of the cluster.

To use K-means clustering, the query or table must have at lease two numeric columns, either measures or dates.

K-means is available as an R template.

{% include note.html content="This algorithm is not on by default. Work with your Customer Success team to enable K-means analysis." %}

{: id="times-series-forecasting"}
## Time series forecasting
Time series forecasting algorithm makes predictions extrapolates the current time series data to make predictions about future events. It uses ARIMA or ETS techniques for modeling the data.

Time series forecasting is available as an R template.

{: id="binomial-logistic-regression"}
## Binomial logistic regression

Logistic regression models the probability of outcome of a categorical dependent variable when all other variables are independent. In a binomial logistic regression, the dependent variable has only two categories. To make the relationship linear, we use the logit link function.

Binomial logistic regression is available as an R template.
