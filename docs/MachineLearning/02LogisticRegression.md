---
layout : default
title : 02 Logistic Regression
nav_order : 2
math: mathjax3
parent : Machine Learning
---

# Logistic Regression
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 0. sigmoid / softmax function

- odds : $(0, 1) \rightarrow (0, \infty)$

$$
\text{odds} = \frac{p}{1 - p}
$$

- logit transformation : $(0, 1) \rightarrow (-\infty, \infty)$

$$
\text{log}(\text{odds}) = \text{log} \frac{p}{1 - p}
$$

- sigmoid function (inverse of logit) : $(-\infty, \infty) \rightarrow (0, 1)$

$$
\sigma(x) = \frac{1}{1 + e^{-x}} = p(y=1 \vert \mathbf{x})
$$

- softmax function (generalized sigmoid) : $(-\infty, \infty)^n \rightarrow (0, 1)^n$

$$
\sigma(\mathbf{x})_i = \frac{e^{x_i}}{\sum_{k=1}^{n} e^{x_k}} = \frac{e^{x_i}}{e^{x_1} + e^{x_2} + \cdots + e^{x_n}}
$$

If $n=2$ (binary, sigmoid)

$$
\sigma({\mathbf{x}})_1 = \frac{e^{x_1}}{e^{x_1} + e^{x_2}} = \frac{1}{1 + e^{x_2 - x_1}} 
$$

thus domain of sigmoid function can be interpreted as the **score difference**.


## 1. model

### binary classification

$$
P(y = 1 \vert \mathbf{x}) 
= \sigma(\mathbf{w}^T \mathbf{x})
= \frac{1}{1 + e^{w_0 + w_1 x_1 + \cdots + w_k x_k}}
$$


### multiple classification

$$
P(y = c_i \vert \mathbf{x})
= \sigma(W \mathbf{x})_i
= \frac{e^{\mathbf{w}_i^T \mathbf{x}}}{e^{\mathbf{w}_1^T \mathbf{x}} + e^{\mathbf{w}_2^T \mathbf{x}} + \cdots + e^{\mathbf{w}_k^T \mathbf{x}}}
,

\quad

W = 
\begin{bmatrix} 
    \mathbf{w}_1^T \\
    \mathbf{w}_2^T \\ 
    \vdots \\
    \mathbf{w}_k^T
\end{bmatrix}
$$

Each $\mathbf{w}_i^T \mathbf{x}$ can be interpreted as the *i*-th class score.


## 2. Decision Boundary

Assume that a data point $\mathbf{x}$ is classified as the *i*-th class if the score $P(y = c_i \vert \mathbf{x}) > p $ for some $p \in (0, 1)$.

Then

$$
P(y = c_i \vert \mathbf{x}) > p
\iff 
\mathbf{w}_i^T \mathbf{x} > c
$$

where $ c = \text{ln}[p(e^{\mathbf{w}_1^T \mathbf{x}} + e^{\mathbf{w}_2^T \mathbf{x}} + \cdots + e^{\mathbf{w}_k^T \mathbf{x}})]$

A hyperplain $ \mathbf{w}_i^T \mathbf{x} = c $ is called **decision boundary**.

|![decision boundary - threshold classification](/docs/MachineLearning/images/decisionboundary_threshold.jpeg)|![decision boundary - max classification](/docs/MachineLearning/images/decisionboundary_max.png)|
|:---:|:---:|
|decision boundary - threshold classification|decision boundary - max classification|


## 3. Loss Function 

### discriminative setting (binary classification)

- ground truth $y \in \{+1, -1\}$
- predicted score $\hat{y} \in \mathbb{R}$
- margin $y \hat{y}$

margin-based loss function

|0/1 loss|log loss|exponential loss|hinge loss|
|:---:|:---:|:---:|:---:|
|$I_{(y\hat{y}<0)}$|$\text{log}(1 + e^{-y \hat{y}})$|$e^{-y \hat{y}}$|$\text{max}\{ 0, 1- y \hat{y} \}$|
|not continuous <br/> not diff'able <br/> at $y \hat{y}=0$|interpretable <br/> $p(y \vert x)$ <br/> (logistic regression)|vulnerable to outliers|computationally efficient <br/> (SVM)|


|![a rough form of graphs](/docs/MachineLearning/images/margin-based_loss_functions.png)|
|:---:|
|a rough form of graphs|

[more margin-based loss function - GitHub blog](http://juliaml.github.io/LossFunctions.jl/stable/losses/margin/)


### probabilistic setting

- ground truth $y \in \{ 0, 1\}$ for a binary classification
- ground truth $\mathbf{y} = (y_k) \in \{ 0, 1 \}^K$ : an one-hot vector for a multi-class classification
- predicted score $\hat{\mathbf{y}} \in [0,1]^K$
- compare two probability distribution, *our model* and *the empirical distribution*  
[information theory](/docs/Statistics/InformationTheory.md#3-cross-entropyhpq-and-mle)

$$
\mathcal{L} = - \frac{1}{m} \sum_{i=1}^{m} \sum_{k=1}^K y_{ik} \text{log}( \hat{y}_{ik} ) = - \frac{1}{m} \sum_{i=1}^m \text{log} ( \hat{y}_{iT_i})
$$

where  
$m$ : number of data,  
$K$ : number of classes, and  
$\hat{y}_{iT_i}$ : predicted probability for the correct class (the degree of certainty).

Interpreting $\dfrac{1}{m}$ as a probability in the empirical distribution $P$, 

$$
\mathcal{L} = H(P, \hat{P})
$$

for our model (estimated distribution) $\hat{P}$.
