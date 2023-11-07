# COMPSCI 273A 
# 10/4
## Inductive bias
- Allow us to extend observed data to unobserved ones
  - interpolation / extrapolation
- What relationship do we expect in the data
  - A key question in ML models
  - Usually, data pull us away from assumptions only with evidence

## Overfitting & Complexity
![image](Overfitting.png)

## Bayes rule
![image](Bayes%20Rule.png)

## Naive Bayes Classifiers
- Independence
- Only need to estimate each individually

Errors:
- type 1: false positive
- type 2: false negative

add multiplier alpha can reduce one kind of error (move decision boundary)

**Sensitivity**: True positive rate \
**Specificity**: True negative rate

## kNN k Nearest Neighbor
Find the k-nearest neighbors to x in the data
- i.e., rank the feature vectors according to Euclidean distance
- select the k vectors which are have smallest distance to x


Regression
- Ranking gives k closest examples and their target values “y”
- Usually just average the y-values of the k closest training examples
- Larger k = average over a larger area for prediction

# 10/09
## Linear Regression
gradient decent vector should always go towards negative
1. initialization
2. step size a
   - can change over iterations
3. Gradient direnction
4. Stopping condition

## Newton's method

## Stochastic gradient decent
to save computationnal time calculate loss for only a few point \
idea is that take average GPA of 1000 students is close enough to GPA for all students \
**MSE is sensitive to outliers** \
**L1 error: Mean absolute error**

# 10/11
In general, can use any feature we think are useful
- Polynomiao function
  - Features [1, x, x^2, x^3]
- Other feature
  - 1/x sqrt(x) x1*x2
- Linear regression = linear in the parameters

## Vanriance and Bias
low bias high varians means low percision but high accuracy (high complexity model)\
high bias low varians means high percision but low accuracy (low complexity model)\
more data can reduce variance. \
bias is from the funtion of the model \

## k fold cross validation
- divide into k disjoint sets
- hold out one set (=M/K DATA) for validation
- Train on the others (= M*(K-1) / K data)

## What to do about under/overfitting?
- ways to increase complexity?
  - add features parameters
  - more to come
- ways to decrease complexity?
  - remove features (feature selection)
  - "Fail to fullu memorize data
    - partial training
    - regularization


# 10/16
## Perceptron = a linear classifier
- The parameters theta are sometimes called weights w
- input x1 .... xn
- define an additional constant input x0

**a data set is separated if all data points can be correctly classified**
  - mixed together data is not separated
  - clearly separated 2 cluster data is separated

**if a data set is not linearly separateable square one feature to create high deminsion**

## Surrogate loss functions

# 10/18
## support vector machine (SVM)
maximize margin
vectir w = [w1, w2, ...] is orthogonal to boundary

# 10/23
soft margin introduce slack variables for violated constrains \
smaller R allows more violation \
dot product of xi and xj is measuring their similarity \

# 10/25
# Hard margin
## Primal (hard to optimize)
arg min w^2
## Lagrangian (ok to optimize)
arg min(theta) max(a) 
## Dual (easy to optimize)
arg max(a >= 0) 

# Soft margin (non linearly separeable data)
surrogate loss (hinge loss)
## lagrangian 
## Dual
arg max (0 <= a <= R)
K(x, x') -> 

# 11/01
VC dimension H describe the number of points that can be shattered by model