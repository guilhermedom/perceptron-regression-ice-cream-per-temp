# Perceptron Regression for Ice Cream Revenue per Temperature

Perceptron regressing revenue for an ice cream stand according to temperature.

---

## Problem Overview

If we observe a significant linear correlation between the two variables, we can say that one can be predicted by the other. There may be a correlation between temperature and the revenue in a stand selling ice cream. We aim to verify that using our [dataset]. Our dataset has only two variables: "Temperature" in degrees Celsius, the independent variable; "Revenue" in dollars, the dependent variable. There are 500 instances with no missing or corrupt values. If both variables are plotted against each other on a scatter plot, a shape similar to a diagonal line is formed, making their linear correlation apparent:

![perceptron_regression_ice_cream_revenue_per_temp_linear_correlation](https://user-images.githubusercontent.com/33037020/210909403-830b2721-e1dd-4eff-a6dc-bef3ca0fb070.PNG)

There is a multitude of algorithms able to model the linear correlation between two variables, like [Ordinary Least Squares] (OLS) linear regression and [Perceptron] linear regression. With only one explanatory variable, any model used falls into the setting of a simple linear regression.

## Analysis Introduction

[Simple linear regression] uses a single independent variable to model a dependent variable. It is applicable in datasets where a single variable has an almost perfect linear correlation with the dependent variable, or when there is only one independent variable available. These linear models are easily trainable and are very efficient.

Simple linear regressors can be described by the following equation:

$$ y = a \cdot x + b $$

where *a* is the coefficient of the independent variable *x* and *b* is the intercept term (or bias).

Perceptrons, neural networks having a single neuron, have been used as regressors since their invention. Sometimes referred to as [Adaline] models, these perceptrons do not have an activation function. This way, their output is directly considered the regression result for a given input value. Note that the equation expressed by this perceptron, considering its weights and bias, is exactly the same equation described above for simple linear regressors.

In this project, we train a perceptron regressor to model the observed (and plotted) linear correlation between temperature and ice cream revenue. We make sure that 6 main linear regression assumptions ([out of many linear regression assumptions]) are respected:

1. There is a linear correlation between the independent and the dependent variables;
2. Multivariate normality, i.e., the set having all variables must follow a multivariate normal distribution;
3. No multicollinearity, meaning that indenpendent variables should not be highly correlated with each other;
4. No autocorrelation, which means that prediction errors, for any instance, must not have any correlation with prediction errors of other instances;
5. Normality of residuals, as prediction errors are assumed to follow a normal distribution;
6. Homoscedasticity, so that prediction errors have a constant variance.

We guarantee that the assumptions are matched using visual breakdowns of the data. For example, the [Q-Q chi-squared probability plot] demonstrates if the squared [Mahalanobis distances] between the data instances and the dataset centroid follow a chi-squared distribution. If that is the case, then the set of all variables in our dataset is multivariate normal, conforming with linear regression's assumption 2.

![perceptron_regression_ice_cream_revenue_per_temp_multivariate_normality](https://user-images.githubusercontent.com/33037020/210903843-9b082451-6f91-4d38-8c64-7f62738b5b56.PNG)

In the end, our **perceptron regressor achieves an almost perfect [R2 score] of 0.98**. The [mean absolute error] for the model is around 18, less than 2% of the revenue range in the dataset: max(revenue) - min(revenue) = 1000 - 10 = 990. The perceptron regressor is also compared with [Scikit-learn's OLS regressor], achieving roughly the same performance.

![perceptron_regression_ice_cream_revenue_per_temp_test_regression](https://user-images.githubusercontent.com/33037020/210903852-a260dd51-1782-4f40-a834-59d491149654.PNG)

[//]: #

[dataset]: <https://www.kaggle.com/datasets/4c8d766e253c62e5910952e619db9267f34c58497a74001571106b157080ee9b?resource=download>
[Adaline]: <https://en.wikipedia.org/wiki/ADALINE>
[Ordinary Least Squares]: <https://www.xlstat.com/en/solutions/features/ordinary-least-squares-regression-ols>
[Perceptron]: <https://en.wikipedia.org/wiki/Perceptron>
[Simple linear regression]: <https://www.scribbr.com/statistics/simple-linear-regression/>
[out of many linear regression assumptions]: <https://towardsdatascience.com/assumptions-of-linear-regression-fdb71ebeaa8b>
[Mahalanobis distances]: <https://en.wikipedia.org/wiki/Mahalanobis_distance>
[Q-Q chi-squared probability plot]: <https://search.r-project.org/CRAN/refmans/heplots/html/cqplot.html>
[Scikit-learn's OLS regressor]: <https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html>
[R2 score]: <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.r2_score.html>
[mean absolute error]: <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_error.html>
