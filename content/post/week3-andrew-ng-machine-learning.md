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


#### Decision Boundary
Let's say we decide the hypothesis is h(x) with θ0 = -3, θ1 = 1 and θ2 = 1. **Decision boundary** is the line when z = θ.T.dot(X) = 0.

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/decision-boundary.JPG?raw=true)


Decision boundary can also be non-linear.It can look like this:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/db1.JPG?raw=true)

Or looks like this:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/db2.JPG?raw=true)

The shape of the decision boundary is decided by z. 