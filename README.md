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

<b>Steps</b><br>
a. We start with creating a dataset of 500 observations, with one informative feature. With only one feature and the target, we plot the data, together with the models’ fits. Also, we specify the noise (standard deviation applied to the output) and create a list containing the coefficient of the underlying linear model, that is, what the coefficient would be if the linear regression model was fit to the generated data. In this example, the value of the coefficient is 64.6. We extract those coefficients for all the models and then use them to compare how well they fit the data.

b. Next, we replace the first 25 observations (5% of the observations) with outliers, far outside of the mass of generated observations. Bear in mind that the coefficient stored earlier comes from the data without outliers. Including them makes a difference.

c.<b>Linear regression</b>
We start with the good old linear regression model, which is likely highly influenced by the presence of the outliers.Then, we prepare an object to use for plotting the fits of the models. The plotline_X object is a 2D array containing evenly spaced values within the interval dictated by the generated data set. We use this object for getting the fitted values for the models. It must be a 2D array, given it is the expected input of the models in scikit-learn.

d.<b>Huber regression</b>
Huber regression is an example of a robust regression algorithm that assigns less weight to observations identified as outliers. To do so, it uses the Huber loss in the optimization routine.

e.You might recognize this approach to loss functions from analyzing the differences between two of the popular regression evaluation metrics: mean squared error (MSE) and mean absolute error (MAE). Similar to what the Huber loss implies, it is recommended to use MAE when you are dealing with outliers, as it does not penalize those observations as heavily as the squared loss does.
Connected to the previous point is the fact that optimizing the squared loss results in an unbiased estimator around the mean, while the absolute difference leads to an unbiased estimator around the median. The median is much more robust to outliers than the mean, so we expect this to provide a less biased estimate.

f.<b>RANSAC regression</b>
Random sample consensus (RANSAC) regression is a non-deterministic algorithm that tries to separate the training data into inliers (which may be subject to noise) and outliers. 

g.<b>Theil-Sen regression</b>
The last of the robust regression algorithms available in scikit-learn is the Theil-Sen regression. It is a non-parametric regression method, which means that it makes no assumption about the underlying data distribution. In short, it involves fitting multiple regression models on subsets of the training data and then aggregating the coefficients at the last step.

<b>In General</b>
In general, robust fitting in a high-dimensional setting is difficult.
In contrast to Theil-Sen and RANSAC, Huber regression is not trying to completely filter out the outliers. Instead, it lessens their effect on the fit.
Huber regression should be faster than RANSAC and Theil-Sen, as the latter ones fit on smaller subsets of the data.
Theil-Sen and RANSAC are unlikely to be as robust as the Huber regression using the default hyperparameters.
RANSAC is faster than Theil-Sen and it scales better with the number of samples.
RANSAC should deal better with large outliers in the y-direction, which is the most common scenario.
