# Regularized-Linear-Regression-and-Bias-v.s.-Variance

In this exercise, you will implement regularized linear regression and use it to study models with different bias-variance properties. Before starting on the programming exercise, we strongly recommend watching the video lectures and completing the review questions for the associated topics. To get started with the exercise, you will need to download the starter code and unzip its contents to the directory where you wish to complete the exercise. If needed, use the cd command in Octave/MATLAB to change to this directory before starting this exercise. You can also find instructions for installing Octave/MATLAB in the “Environment Setup Instructions” of the course website. 

## Files included in this exercise

ex5.m - Octave/MATLAB script that steps you through the exercise
ex5data1.mat - Dataset
submit.m - Submission script that sends your solutions to our servers
featureNormalize.m - Feature normalization function
fmincg.m - Function minimization routine (similar to fminunc)
plotFit.m - Plot a polynomial fit
trainLinearReg.m - Trains linear regression using your cost function

[1] linearRegCostFunction.m - Regularized linear regression cost function
[2] learningCurve.m - Generates a learning curve
[3] polyFeatures.m - Maps data into polynomial feature space
[4] validationCurve.m - Generates a cross validation curve

Throughout the exercise, you will be using the script ex5.m. These scripts
set up the dataset for the problems and make calls to functions that you will
write. You are only required to modify functions in other files, by following
the instructions in this assignment.

## 1. Regularized Linear Regression
In the first half of the exercise, you will implement regularized linear regression to predict the amount of water flowing out of a dam using the change of water level in a reservoir. In the next half, you will go through some diagnostics of debugging learning algorithms and examine the effects of bias v.s. variance. The provided script, ex5.m, will help you step through this exercise.

## 2. Bias-variance
An important concept in machine learning is the bias-variance tradeoff. Models with high bias are not complex enough for the data and tend to underfit, while models with high variance overfit to the training data.

## 3. Polynomial regression
The problem with our linear model was that it was too simple for the data
and resulted in underfitting (high bias). In this part of the exercise, you will
address this problem by adding more features.
For use polynomial regression, our hypothesis has the form:

hθ(x) = θ0 + θ1 ∗ (waterLevel) + θ2 ∗ (waterLevel)2 + · · · + θp ∗ (waterLevel)p
= θ0 + θ1x1 + θ2x2 + ... + θpxp.

Notice that by defining x1 = (waterLevel), x2 = (waterLevel)2
, . . . , xp = (waterLevel)p, we obtain a linear regression model where the features are the
various powers of the original value (waterLevel).

Now, you will add more features using the higher powers of the existing
feature x in the dataset. Your task in this part is to complete the code in
polyFeatures.m so that the function maps the original training set X of size
m × 1 into its higher powers. Specifically, when a training set X of size m × 1
is passed into the function, the function should return a m×p matrix X poly,
7
where column 1 holds the original values of X, column 2 holds the values of
X.^2, column 3 holds the values of X.^3, and so on. Note that you don’t
have to account for the zero-eth power in this function.
Now you have a function that will map features to a higher dimension,
and Part 6 of ex5.m will apply it to the training set, the test set, and the
cross validation set (which you haven’t used yet).
