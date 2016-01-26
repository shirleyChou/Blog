+++
author = "ZHOUYI"
comments = true
date = "2016-01-25T14:03:34+08:00"
draft = false
menu = ""
share = true
slug = "linear-regression-with-one-variable"
tags = ["Machine Learning", "Coursera", "Andrew Ng"]
title = "Linear Regression with One Variable"
description = "Week 1"
+++

## Introduction
#### What is machine learning?
* **DEFINITION**:   
  Tom Mitchell (1998) Well-posed Learning Problem: A computer program is said to learn from **experience E** with respect to some **task T** and some **performance measure P**, if its performance on T, as measured by P, improves with experience E.

* **EXAMPLE**:    
  Suppose your email program watches which emails you do or do not mark as spam, and based on that learns how to better filter spam. What is the task T in this setting?
  
  * Classifying emails as spam or not spam ( **T** )
  * Watching you label emails as spam or not spam ( **E** )
  * The number (or fraction) of emails correctly classified as spam/not spam ( **P** )


#### Several types of machine learning algorithms
* **Supervised Learning**
  Given the “right answer” for each example in the data.
  * **Regression problem**
    * Predict **continuous** valued output
  * **Classification problem**
    * Predict **discrete** valued output
* **Unsupervised Learning**
  Let the computer learn how to do something by thenselves.
  * **Clustering problem**
* **Reinforcement learning**
* **Semi-supervised Learning**


## Linear Regression with One Variable
Linear Regression with one variable also call **Univariate linear regression**. 

### Hypothesis
Housing price data example used earlier:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/house-prices.JPG?raw=true)

And the **HYPOTHESIS** for linear regression is:   
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/hypo.JPG?raw=true)

Which theta0 and theta1 are the **PARAMETERS**.


### Cost function
The idea is to choose theta_0, the_1 so that hypothesis h is **CLOSE** to y for our training examples(x, y). And how do we determine parameters theta? Use **COST FUNCTION**:  
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/cost.JPG?raw=true)

So **This is** a minimization problem and our **GOAL** is to minimize the Cost function:  
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/goal.JPG?raw=true)

##### parameters explanation:    
* This is called Squared error function
* 1/2m
  * 1/m - means we determine the average
  * 1/2 - the 2 makes the math a bit easier, and doesn't change the constants we determine at all (i.e. half the smallest value is still the smallest value!)
* Minimizing θ0/θ1 means we get the values of θ0 and θ1 which find on average the minimal deviation of x from y when we use those parameters in our hypothesis function

#### Recap:
* Hypothesis: like your prediction machine, throw in an x value, get a putative y value
* Cost: a way to, using your training data, determine values for your θ values which make the hypothesis as accurate as possible
  * Also called the squared error cost function
  * This cost function is reasonable choice for most regression functions
  * Probably most commonly used function


### A deeper insight into the cost function
So we know that the cost function determines parameters. In order to visualize cost function J a little bit easier, we assume θ0 = 0 and now the goal is to minimize cost function J(θ1). If we compute a range of values plot, we get a polynomial (looks like a quadratic):

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/theta_1.JPG?raw=true)

The optimization objective for the learning algorithm is to find the value of θ1 which minimizes J(θ1). θ1 = 1 is the best value for θ1 here.

Now we use our original complex hypothesis with two variables: J(θ0, θ1) and draw a **3D surface plot**:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/surface-plot.JPG?raw=true)

##### Notice
* the height(y) indicates the value of the cost function, so the goal is to find where y is at a minimum.

And also, we can plot a **contour plots** for better intuition:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/contour.JPG?raw=true)

##### Notice
* each color is the same value of J(θ0, θ1), but obviously plot to different locations because θ1 and θ0 will vary
* each point (like the pink one above) represents a pair of parameter values for Ɵ0 and Ɵ1
* Finding Ɵ0 and Ɵ1 by eye/hand is in pain. What we really want is an efficient algorithm


### Gradient descent algorithm
#### Outline
* Start with some θ0, θ1
* Keep changing θ0, θ1 to reduce J(θ0, θ1) until we hopefully end up at a minimum
* And **GRADIENT DESCENT** do that work!

#### How does it work?
* Start with initial guesses (0,0 (or any other value))
* Keeping changing θ0 and θ1 a little bit to try and reduce J(θ0, θ1). Each time you change the parameters, you select the gradient which reduces J(θ0,θ1) the most possible
* Repeat
* Do so until converge to a local minimum

#### The definition of gradient descent algorithm
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/grad.JPG?raw=true)

##### parameters explanation:
* **derivative term**: 
    * Remember to use **partial derivative** when we have multiple variables but only derive with respect to one.
    * Despite the value of x (positive or negative), J(θ) will always reduce. 
    ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/derivative.JPG?raw=true)

* **alpha (learning rate)**: 
    * When you get to a local minimum, gradient of tangent/derivative is 0. So derivative term = 0 and theta remains the same. 
    ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/learning-rate.JPG?raw=true)
    * As we approach a local minimum, gradient descent will automatically take smaller steps. So no need to decrease alpha over time.  
    ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/smallstep.JPG?raw=true)
  

##### Notice!
* **HAVE TO SIMULTANEOUSLY** update j = 0 and j = 1. If you implement the non-­simultaneous update it's not gradient descent, and will behave weirdly.  
  ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/theta_update.JPG?raw=true)

* An interesting property: **Where you start** can **determine** which minimum you may end up
  ![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/local-minimum.JPG?raw=true)

#### "Batch" Gradient Descent
“Batch”: Each step of gradient descent uses all the training examples.


### Linear regression with gradient descent
Apply gradient descent to minimize the squared error cost function J(θ0, θ1). When we derive this expression in terms of j = 0 and j = 1 we get the following:
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/derive-cost.JPG?raw=true)

Since the **linear regression** cost function is always a convex function(Bowl shaped), So gradient descent will always converge to **global optima**. 


### Important extensions
There exists a **numerical solution** for finding a solution for a minimum function - **Normal equation**. Both these two methods can solve the minimization problem. 

#### Pros and cons of Normal equation
* Advantage
    * No longer an alpha term
    * Can be much faster for some problems
* Disadvantage
    * much more complicated
