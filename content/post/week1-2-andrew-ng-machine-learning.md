+++
author = "ZHOUYI"
comments = true
date = "2016-01-25T14:03:34+08:00"
draft = false
menu = ""
share = true
slug = "week1and2-linear-regression"
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


### Linear Regression 
Linear Regression with one variable also call **Univariate linear regression**. 

#### Hypothesis
Housing price data example used earlier:
![](https://github.com/shirleyChou/my-blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/house-prices.JPG?raw=true)

And the **HYPOTHESIS** for linear regression is as follows, which theta are the parameters.    
![](https://github.com/shirleyChou/my-blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/hypo.JPG?raw=true)

#### Cost function
The idea is to choose theta_0, the_1 so that hypothesis h is **CLOSE** to y for our training examples(x, y). So **This is** a minimization problem. Our goad is to minimize:        ![](https://github.com/shirleyChou/my-blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/bias.JPG?raw=true). 

And we named the part that plan to minimize **COST FUNCTION**.      
![](https://github.com/shirleyChou/my-blog/blob/master/static/content/post/images/andrew-ng-ml/week1-2/cost.JPG?raw=true)

##### parameters explanation:    
* This is called Squared error function
* 1/2m
  * 1/m - means we determine the average
  * 1/2 - the 2 makes the math a bit easier, and doesn't change the constants we determine at all (i.e. half the smallest value is still the smallest value!)
* Minimizing theta_0/theta_1 means we get the values of theta_0 and theta_1 which find on average the minimal deviation of x from y when we use those parameters in our hypothesis function

#### Recap:
* Hypothesis: like your prediction machine, throw in an x value, get a putative y value
* Cost: a way to, using your training data, determine values for your θ values which make the hypothesis as accurate as possible
  * Also called the squared error cost function
  * This cost function is reasonable choice for most regression functions
  * Probably most commonly used function
