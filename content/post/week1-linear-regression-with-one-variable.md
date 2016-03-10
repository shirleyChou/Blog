+++
author = "ZHOUYI"
comments = true
date = "2016-01-25T14:03:34+08:00"
draft = false
menu = ""
share = true
slug = "linear-regression"
tags = ["Machine Learning", "CS 229", "Andrew Ng"]
title = "Linear Regression with one variable"
description = "Week 1"
+++

Let’s start by talking about a few examples of supervised learning problems. Suppose we have a dataset giving the living areas and prices of 47 houses from Portland, Oregon:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/house-prices.JPG?raw=true)

To establish notation, use **x(i)**(above) to denote the "input" variables (living area in this example), also called **input features**, and **y(i)** to denote the “output” or **target variable** that we are trying to predict(price). A pair **(x(i), y(i))** is called a **training example**. And use ***X*** denote the space of input values, ***Y*** the space of output values. In this example, ***X*** = ***Y*** = ***R***.

And the goal is, given a training set, to learn a function h : ***X*** → ***Y*** so that h(x) is a "good" predictor for the corresponding value of y. This function *h* is called a **hypothesis**.

To perform supervised learning, we must decide how we’re going to represent functions/hypotheses h in a computer. As an initial choice, let’s say we decide to approximate y as a linear function of x:  
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/hypo.JPG?raw=true)  
Here, the θi’s are the **parameters**(also called weights) parameterizing the space of linear functions mapping from ***X*** to ***Y***.


### Cost function
Now, given a training set, how do we pick, or learn, the parameters θ? One reasonable method seems to be to make h(x) close to y, at least for the training examples we have. To formalize this, we will define a function that measures, for each value of the θ’s, how close the h(x(i))’s are to the corresponding y(i)’s. We define the cost function:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/cost.JPG?raw=true)

##### Parameters explanation:    
* This is called Squared error function
* 1/2m
  * 1/m - means we determine the average
  * 1/2 - the 2 makes the math a bit easier, and doesn't change the constants we determine at all (i.e. half the smallest value is still the smallest value!)
* Minimizing θ0/θ1 means we get the values of θ0 and θ1 which find on average the minimal deviation of x from y when we use those parameters in our hypothesis function


##### Cost function intuition:
* Cost function is a way to, using your training data, determine values for your θ values which make the hypothesis as accurate as possible
* It also called the squared error cost function
* This cost function is reasonable choice for most regression functions. And is probably most commonly used function


### A deeper insight into the cost function
So we know that the cost function determines parameters. In order to visualize cost function J a little bit easier, we assume θ0 = 0 and now the goal is to minimize cost function J(θ1). If we compute a range of values plot, we get a polynomial (looks like a quadratic):

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/theta_1.JPG?raw=true)

The optimization objective for the learning algorithm is to find the value of θ1 which minimizes J(θ1). θ1 = 1 is the best value for θ1 here.

Now we use our original complex hypothesis with two variables: J(θ0, θ1) and draw a **3D surface plot**:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/surface-plot.JPG?raw=true)

##### Notice
* the height(y) indicates the value of the cost function, so the goal is to find where y is at a minimum.

And also, we can plot a **contour plots** for better intuition:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/contour.JPG?raw=true)

##### Notice
* each color is the same value of J(θ0, θ1), but obviously plot to different locations because θ1 and θ0 will vary
* each point (like the pink one above) represents a pair of parameter values for Ɵ0 and Ɵ1
* Finding Ɵ0 and Ɵ1 by eye/hand is in pain. What we really want is an efficient algorithm



## LMS algorithm
We want to choose θ so as to minimize J(θ). Specifically, let’s consider the **gradient descent algorithm**.

### Gradient descent algorithm
#### How does it work?
* Start with initial guesses (0,0 (or any other value))
* Keeping changing θ0 and θ1 a little bit to try and reduce J(θ0, θ1). Each time you change the parameters, you select the gradient which reduces J(θ0,θ1) the most possible
* Repeat
* Do so until hopefully converge to a value of θ that minimizes J(θ)

#### The definition of gradient descent algorithm
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/grad.JPG?raw=true)

##### Parameters explanation:
* **Alpha (learning rate)**: 
    * When you get to a local minimum, gradient of tangent/derivative is 0. So derivative term = 0 and theta remains the same. 
    ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/learning-rate.JPG?raw=true)
    * As we approach a local minimum, gradient descent will automatically take smaller steps. So no need to decrease alpha over time.  
    ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/smallstep.JPG?raw=true)

* **derivative term**: 
    * Remember to use **partial derivative** when we have multiple variables but only derive with respect to one.
    * Despite the value of x (positive or negative), J(θ) will always reduce. 
    ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/derivative.JPG?raw=true)
  

##### Notice!
* **HAVE TO SIMULTANEOUSLY** update j = 0 and j = 1. If you implement the non-­simultaneous update it's not gradient descent, and will behave weirdly.  
  ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/theta_update.JPG?raw=true)

* An interesting property: **Where you start** can **determine** which minimum you may end up
  ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/local-minimum.JPG?raw=true)

#### "Batch" Gradient Descent
“Batch”: Each step of gradient descent uses all the training examples.


### Linear regression with gradient descent
Apply gradient descent to minimize the squared error cost function J(θ0, θ1). When we derive this expression in terms of j = 0 and j = 1 we get the following:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1/derive-cost.JPG?raw=true)

Since the **linear regression** cost function is always a convex function(Bowl shaped), So gradient descent will always converge to **global optima**. 
