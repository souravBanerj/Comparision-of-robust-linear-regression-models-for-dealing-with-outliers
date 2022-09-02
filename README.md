# Comparision-of-robust-linear-regression-models-for-dealing-with-outliers

1.Linear regression is one of the simplest machine learning models out there. It is often the starting point notonly for learning about data science but also for 
building quick and simple minimum viable products (MVPs), which then serve as benchmarks for more complex algorithms.

2.In general, linear regression fits a line (in two dimensions) or a hyperplane (in three and more dimensions) that best describes the linear relationship between 
the features and the target value. The algorithm also assumes that the probability distributions of the features are well-behaved; for example, they follow 
the Gaussian distribution.

3.Outliers are values that are located far outside of the expected distribution. They cause the distributions of the features to be less well-behaved. As a consequence, 
the model can be skewed towards the outlier values, which, as we’ve already established, are far away from the central mass of observations.
Naturally, this leads to the linear regression finding a worse and more biased fit with inferior predictive performance.

4.It is important to remember that the outliers can be found both in the features and the target variable, and all the scenarios can worsen the performance of the model.

5.There are many possible approaches to dealing with outliers: removing them from the observations, treating them (for example, capping the extreme observations at a 
reasonable value), or using algorithms that are well-suited for dealing with such values on their own. This post focuses on these robust methods.

<b>Steps</b>
