+++
author = "ZHOUYI"
comments = true
date = "2016-02-23T18:02:35+08:00"
draft = false
image = ""
menu = ""
share = true
slug = "machine-learning-concepts"
tags = ["Machine Learning", "Coursera", "Andrew Ng"]
title = "Machine learning concepts"

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
    The target variable that we’re trying to predict is continuous
    * **Classification problem**  
    The target variable that we’re trying to predict is discrete
* **Unsupervised Learning**  
  Let the computer learn how to do something by thenselves.
    * **Clustering problem**
* **Reinforcement learning**
* **Semi-supervised Learning**