# Introduction

## What is Machine Learning?
Machine Learning is the subfield of computer science that gives “computers the ability to learn without being explicitly programmed.”
## Categorization of machine learning systems
### Whether or not they are trained with human supervision
1. Supervised learning
  
    k-nearest neighbors, Linear regression, Logistic regression, Support vector machines (SVM), Decision trees, Random forests, Neural networks
1. Unsupervised learning
   + Clustering

        k-Means, Hierarchical Cluster Analysis (HCA), Expectation maximization, Visualization and Dimensionality Reduction, Principal Component Analysis (PCA), Kernel PCA, Locally-Linear Embedding (LLE),t-distributed Stochastic Neighbor Embedding (t-SNE)
    + Visualization and Dimensionality Reduction

        Principal Component Analysis (PCA)
, Kernel PCA, Locally-Linear Embedding (LLE), t-distributed Stochastic Neighbor Embedding (t-SNE)
    + Association Rule Learning
  
        Apriori, Equivalence Class Learning (Eclat)
1. Semisupervised learning
2. Reinforcement learning
   
    chess AI
### Whether or not they can learn incrementally
1. Online learning
2. Batch learning
### Whether they work by comparing new data points to previously known data points or by detecting patterns and building a predictive model.
1. Instance-based learning
2. Model-based learning

## Types of parameters
### Model parameters

Parameters learned through model training

E.g. Slope and intercept of the result of a least-squares fit to the training data 

### Hyperparameters

Parameters that define the model or how model training occurs

E.g. Training or learning rate
Number of leaves of depth of a tree
Number of hidden layers in a deep neural network
Number of clusters in a k-mean clustering


## Principal challenges in machine learning
+ Insufficient training data
+ Non-representative training data
+ Incomplete or poor quality data
+ Irrelevant features
+ Over-fitting the training data
+ Under-fitting the training data
+ Non-stationary data
+ Some models are “black boxes”

## Trusim
### No Free Lunch Theorem
+ If you make absolutely no assumptions about the
data, then there is no reason to prefer one model
over another.
+ That is, one size does not fit all.
+ Proved by David Wolpert in 1996.

### Ockham Razor (sometimes Occam’s Razor)
+ The principle that given multiple explanations for an occurrence, the simpler one is usually better.
+ Attributed to William of Ockham (c. 1287 – 1347)
+ Note that a “razor” is a principle or rule of thumb.