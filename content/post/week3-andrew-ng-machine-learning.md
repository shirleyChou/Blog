+++
author = ""
comments = true
date = "2016-03-08T17:54:57+08:00"
draft = false
image = ""
menu = ""
share = true
slug = "logistic-regression"
tags = ["Machine Learning", "Coursera", "Andrew Ng"]
title = "Logistic Regression"

+++

### Logistic Regression Model
Logistic regression is a classification algorithm. It generates a value where is between 0 and 1.

And the hypothesis(function) of logistic regression is:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/function.JPG?raw=true)

i.e.

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/hypothesis.JPG?raw=true)

The hypothesis is alse called "**Sigmoid function**", or "**Logistic function**". The term `Logistic function` is what give rise to the name logistic progression. The term `Sigmoid function` and the term `Logistic function` are basically synonyms and mean the same thing. So either term can be used to refer to the function g.

The **Sigmoid function** looks like:  
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/graph.JPG?raw=true)

##### So, when make predictions that y = 1(or 0)?
* when g(z) ≥ 0.5, z ≥ 0, predict "y = 1"
* when g(z) ≤ 0.5, z ≤ 0, predict "y = 0"


#### Interpretation of Hypothesis Output
When hypothesis outputs some number, we going to treat that number as the estimated probability that Y = 1 on a new input example X. Here is an example (y = 1 === malignant):

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/example.JPG?raw=true)

To write in more formally, we say hypothesis h(x) is the probability that y = 1, given x,
parameterized by theta:
> h(x) = P(y = 1 | x; theta) = 0.7

So, we also know that:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/probability.JPG?raw=true)

The first equation is saying that the probability of Y equals zero for a particular patient with feature x, plus probability of Y equals one for that same patient must add up to one.


### Decision Boundary
Let's say we decide the hypothesis is h(x) with θ0 = -3, θ1 = 1 and θ2 = 1. **Decision boundary** is the line when z = θ.T.dot(X) = 0.

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/decision-boundary.JPG?raw=true)


Decision boundary can also be non-linear.It can look like this:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/db1.JPG?raw=true)

Or looks like this:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/db2.JPG?raw=true)

The shape of the decision boundary is decided by z. 


### Cost function
We cannot use the cost function of linear regression for logistic regression, since the cost function of linear regression with hypothesis of logistic regression would be a **non-convex** function of the parameters theta. So it **not guarantee to converge to the global minimum**.

Cost function of linear regression below:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/linear-cost-function.JPG?raw=true)

**The meaning of non-convex** is that it could have many **local optima**. And **non-convex** is its formal term.

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/not-convex.JPG?raw=true)


The cost function that is **"convex"** for the cost function is:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/cost-function-logistic.JPG?raw=true)

And we plot these two cost function respectively when y = 1 and y = 0.

If y = 1:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/y=1.JPG?raw=true)

If y = 0:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/y=0.JPG?raw=true)


### Simplified cost function and gradient descent
So, combine y we can get the cost function of logistic regression as follows:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/combine.JPG?raw=true)

And the goal is to minimize J of theta to get parameters θ, and then use those parameters to make a prediction given new x.

**Gradient descent** for cost function of logistic regression is:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/grad.JPG?raw=true)

**Algorithm looks identical to linear regression!**

Question: how to monitor gradient descent to make sure it's conversion correctly.


### Advanced optimization
some advanced optimization algorithms and some advanced optimization concepts.