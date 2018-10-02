---
layout: post
title: Feature Scaling in Python with scikit-learn
featured-img: featureScaling
---

The 4 common methods of feature scaling that are implemented in scikit-learn are:

* StandardScaler
* MinMaxScaler
* RobustScaler
* Normalizer


#### Standard Scaler
The StandardScaler assumes your data is normally distributed within each feature and will scale them such that the distribution is now centred around 0, with a standard deviation of 1.

The mean and standard deviation are calculated for the feature and then the feature is scaled based on:

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler.png" width="25%"></p>

If data is not normally distributed, this is not the best scaler to use.

Let’s take a look at it in action:

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler1.png" width="75%"></p>

All features are now on the same scale relative to one another.

#### Min-Max Scaler
The **MinMaxScaler** is the probably the most famous scaling algorithm, and follows the following formula for each feature:

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler2.png" width="25%"></p>

It essentially shrinks the range such that the range is now between 0 and 1 (or -1 to 1 if there are negative values).

This scaler works better for cases in which the standard scaler might not work so well. If the distribution is not Gaussian or the standard deviation is very small, the min-max scaler works better.

However, it is sensitive to outliers, so if there are outliers in the data, you might want to consider the Robust Scaler below.

For now, let’s see the min-max scaler in action

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler3.png" width="75%"></p>

Notice that the skewness of the distribution is maintained but the 3 distributions are brought into the same scale so that they overlap.

#### Robust Scaler
The **RobustScaler** uses a similar method to the Min-Max scaler but it instead uses the interquartile range, rathar than the min-max, so that it is robust to outliers. Therefore it follows the formula:

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler4.png" width="25%"></p>

For each feature.

Of course this means it is using the less of the data for scaling so it’s more suitable for when there are outliers in the data.

Let’s take a look at this one in action on some data with outliers

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler5.png" width="75%"></p>


Notice that after Robust scaling, the distributions are brought into the same scale and overlap, but the outliers remain outside of bulk of the new distributions.

However, in Min-Max scaling, the two normal distributions are kept seperate by the outliers that are inside the 0-1 range.

#### Normalizer
The normalizer scales each value by dividing each value by its magnitude in n-dimensional space for n number of features.

Say your features were x, y and z Cartesian co-ordinates your scaled value for x would be:

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler6.png" width="25%"></p>

Each point is now within 1 unit of the origin on this Cartesian co-ordinate system.

<p align="center"> <img src="/assets/blog_images/Feature_scaling/StdScaler7.png" width="75%"></p>


Note that the points are all brought within a sphere that is at most 1 away from the origin at any point. Also, the axes that were previously different scales are now all one scale.
