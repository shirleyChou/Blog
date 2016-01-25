+++
author = "ZHOUYI"
comments = true
date = "2016-01-25T14:03:34+08:00"
draft = false
menu = ""
share = true
slug = "week1t&2-linear-regression"
tags = ["Machine Learning", "Coursera", "Andrew Ng"]
title = "Introduction regression analysis and gradient descent"
description = "Week 1&2"
+++

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

### Linear Regression with one variable
Also call **Univariate linear regression**. 

#### Hypothesis
Housing price data example used earlier:
![](https://github.com/shirleyChou/my-blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/house-prices.JPG?raw=true)

And the **HYPOTHESIS** for linear regression learning algorithm is:
![](https://github.com/shirleyChou/my-blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/hypothesis.JPG?raw=true)

#### Cost function  
So the idea is to choose theta_0, the_1 so that hypothesis h is close to y for our training examples(x, y). e.t. **This is** a minimization problem. The goad is to minimize ![equation](http://latex.codecogs.com/gif.latex?(h_{\theta}(x)-y)^2), or the sumation of n numbers divided by n.
