+++
author = "ZHOUYI"
comments = true
date = "2016-01-26T17:25:34+08:00"
draft = false
menu = ""
share = true
slug = "linear-regression-with-multiable-variable"
tags = ["Machine Learning", "Coursera", "Andrew Ng"]
title = "Linear Regression with multiable Variable"
description = "Week 2"
+++

### Multiple features
Multiple features equals to multiple variables.
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/mul-variable.JPG?raw=true)

And definitely, the **HYPOTHESIS** of linear regression would change:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/hypothesis.JPG?raw=true)

where theta are parameters.

### Gradient descent for multiple variables
so as the number of parameter grows, remember to simultaneously update theta_j for j = 0,...,n
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/grad.JPG?raw=true)

where **COST FUNCTION** is still the same:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/cost.JPG?raw=true)

### Gradient descent in practice I
#### Feature Scaling
* The idea of Feature Scaling is to make sure features are on a similar scale, then gradient descents can converge more quickly.
  ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/feature-scaling.JPG?raw=true)

* More generally, get every feature into approximately a -1 ≤ x ≤ 1 range.

  ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/range.JPG?raw=true)

#### Mean normalization
In addition to dividing by so that teh maximum value when performing feature scaling sometimes people will also do what's call mean normalization, which means that replace x with x - μ to make features have approximately zero mean(Do not apply to x0 = 1)

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/mean-normalization.JPG?raw=true)

##### Parameters explanation:
* μ1 - the average value of x in the training set
* s1 - the range(max - min) of values of that feature


### Gradient descent in practice II
#### So in gradient descent, how do we make sure gradient descent is working correctly?
Here is something we can do. We know that the job of gradient descent is to find the theta for you that, you know, hopefully minimizes the cost function j of theta. So we pluck the cost function j of theta as the gradient descent runs. And plot that maybe looks like this:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/decrease.JPG?raw=true)

So what this plot is showing, **is it's showing the value of your cost function after each iteration of gradient descent, and the gradient descent is working properly, then J of theta should decrease after every iteration**.

In this case, we can tell gradient descent is not working
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/not-working.JPG?raw=true)


And one useful thing that this should of plot can tell you also is that by the time you've gotten out to maybe between three hundred and four hundred iterations, it looks like that J of theta hasn't gone down much more. So it looks like that that J of theta have more or less converged because your cost function isn't going down much more. **So looking at the figure can also help you judge whether or not gradient descent has converged**.

By the way, the number of iterations that gradient descent takes to converge for a particular application can vary a lot. So it is hard to tell how many iteration gradient descent needs to converge, and is usually by plotting this sort of plot to try to tell if gradient descent has converged. 

It is also possible to come up with **automatic convergence test**, namely to have a algorithm to try to tell you if gradient descent has converged. Say we can declare convergence if J of theta decreases by less than 10^(-3) in one iteraion. But the threshold is very difficult to decide. So maybe simply plot the figure is a proper choice.

#### How to choose learning rate alpha?
If alpha is too small, slow convergence. if alpha too large: J of theta may not decrease on every iteraion or may not converge.

So when run gradient descent, try a range of values: 0.001, 0.003, 0.01, 0.03, 0.1, 0.3, 1 and pick the alpha seems to be causing J of theta to decrease rapidly.


### Features and polynomial regression
How to get different algorithm, sometimes very powerful ones by choosing appropriate features.

Suppose for housing prices prediction problem, we have two features: frontage, depth. But when we apply linear regression, you don't necessary have to use the exactly features x1 and x2 but can create new features by yourself.
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/area.JPG?raw=true)

So sometimes by defining new features you might actually get a better model. Closing to the idea of choosing features is this idea called polynomial regression. Let's say your house price looks like this:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/quad-and-cubic.JPG?raw=true)

we can apply quadratic function or cubic function, but both of these function may not be ideal. When we use cubic function, x1, x2 and x3 take a very diffierent ranges of values, and it's important to use feature scaling if using gradient descent.

So we may find another reasonable choice like this:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week2/ideal.JPG?raw=true)

We do have a broad choice on feature choosing for models.


### Normal equation
Normal equation: Method to solve for analytically

