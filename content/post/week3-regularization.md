+++
author = ""
comments = true
date = "2016-03-10T11:23:42+08:00"
draft = false
image = ""
menu = ""
share = true
slug = "regularization"
tags = ["Machine Learning", "Coursera", "Andrew Ng"]
title = "Regularization"

+++

#### The problem of overfitting
**Underfitting**: also called "High bias(preconception)", which mean that it's not even fitting the training data very well.

Example of linear regression:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/underfit.JPG?raw=true)

Example of logistic regression:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/underfit-logistic.JPG?raw=true)

**Overfitting**: If we have too many features, the learned hypothesis may fit the training set very well (J(θ) ≈ 0), but fail to generalize(how well a hypothesis applies even to new example) to new examples (predict prices on new examples).

Example of linear regression:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/overfit.JPG?raw=true)

Example of logistic regression:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/overfit-logistic.JPG?raw=true)


#### Addressing overfitting
**Plotting the hypothesis** can be one way to decide what degree polynomial to use. But it cannot often work, because often we have learning problems that where we just have a lot of features and it would be much harder to visualize the data. 

##### So some options are:  
* **Reduce number of features**.  
     * Manually select which features to keep(it may throw away some informations your have about the problem).  
     * Model selection algorithm (later in course).  

* **Regularization**.  
     * Keep all the features, but reduce magnitude/values of parameters θj.  
     * Works well when we have **a lot of features**, each of which contributes a bit to predicting *y*.   


### Regularization
Regularization is a way to address overfitting by making the value of parameters theta really small. so:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/intuition.JPG?raw=true)

What regularization does it to add a regularization term to the cost function J of theta, and **λ** is called **regularization parameter**. And what λ does it controls a trade off between two different goals. The goal of the regularization term is to keep the parameters small, and thus keep the hypothesis relatively simple to avoid overfitting. The first term of the cost function is to fit the training set well.


##### But What if λ is set to an extremely large value (perhaps for too large for our problem, say λ = 10^(10))?

Then θ1, θ2, θ3, θ4... ≈ 0, hypothesis h may be underfitting (become horizontal flat line). For regularization to work well. some care should be taken, to choose a good choice for the regularization parameter λ as well.


### Regularized linear regression
The goal is to minimize J of theta, **be aware of that j is starting from 1!** 

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/regularization.JPG?raw=true)

**Gradient descent** for regularized logistic regression is:

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/theta0.JPG?raw=true)
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/thetaj.JPG?raw=true)

The first term (1 - α * λ / m) < 1, so theta J times a term which is less than one has the effect of shrinking theta J a little bit towards 0. So this makes theta J a bit smaller.

**Normal equation**
![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/normal.JPG?raw=true)

**Suppose m (#examples) ≤ n (#features)**, i.e. you have lots of features in a relatively small training set, θ would be non-invertible/singular

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/theta.JPG?raw=true)

But if λ > 0, θ with **regularization term is invertible**.

![](https://github.com/shirleyChou/blog/blob/master/static/content/post/images/andrew-ng-ml/week3/theta-invertible.JPG?raw=true) 


### Regularized logistic regression
The cost function and the gradient descent(or maybe using Advanced optimization) is the same as Regularized linear regression except the hypothesis is **Sigmoid function**!