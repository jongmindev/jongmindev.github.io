---
layout : default
title : 05 Ensemble
nav_order : 5
math: mathjax3 
parent : Machine Learning
---

# Ensemble
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Bagging (decrease variance) : Bootstrapping + Aggregating 

### (1) What is Bagging?

- Bootstrapping : generate new traing sets by **uniformly sampling with replacement** from the standard traing set  
(cf) bootstrap (n.) : better oneself by rigorous, unaided effort [(Source)](https://www.etymonline.com/search?q=bootstrap)
- Aggregating : aggregate the results of multiple models.  
- (ex) Random Forest  

|![bagging flow](/docs/MachineLearning/images/bagging.png)|
|:---:|
|bagging flow. [(Source)](https://corporatefinanceinstitute.com/resources/knowledge/other/bagging-bootstrap-aggregation/)|


### (2) Statistics - variance reduction

Let $X_1, X_2, \cdots, X_n$ be samples from identical distribution with a variance $\sigma^2$.

For sample mean $\overline{X} = \dfrac{1}{n} \sum\limits_{i=1}^n X_i$,  

$$
\begin{align*}
    \text{Var}(\overline{X}) 
    &= \text{Var}(\dfrac{1}{n} \sum\limits_{i=1}^n X_i) \\
    &= \frac{1}{n^2} \left( \sum_{i=1}^n \text{Var}(X_i) + \sum_{i \ne j} \text{Cov}(X_i, X_j) \right) \\
    &= \frac{1}{n^2} \big( n \sigma^2 + n(n-1) \rho \sigma^2 \big) \\
    &= \rho \sigma^2 + \frac{1}{n} (1-\rho) \sigma^2 \\
    &\lt \rho \sigma^2 + (1 - \rho) \sigma^2 \\
    &= \sigma^2
\end{align*}
$$

where $\rho$ is the pairwise correlation, if $n \ge 2$ and $\rho \ne 1$ (multiple and different samples).  
(assuming each pairwise correlation $\rho$ is same)

Thus by bagging, sampling and averaging, **we obtain an ensemble model with lower variance and the same bias**.

Recall, 

|Algorithm|Bias|variance|
|:---:|:---:|:---:|
|Decision Tree|low|high|
|Linear Regression|high|low|

> That is why the effect of using Bagging together with Linear Regression is low. [(Source)](https://towardsdatascience.com/understanding-the-effect-of-bagging-on-variance-and-bias-visually-6131e6ff1385)

On the other hand, 

$$
\begin{align}
    \text{Var}(\overline{X}) 
    &= \rho \sigma^2 + \frac{1}{n} (1-\rho) \sigma^2 \\
    &= \frac{1}{n} \sigma^2 + \rho \left(1 - \frac{1}{n} \right) \sigma^2
\end{align}
$$

**Property 1**  
From the equation $(1)$, **the more sub-model** ($n$), **the lower variance**.  

**Property 2**  
From the equation $(2)$, **the lower correlation between sub-models** ($\rho$), **the lower variance**.


### (3) Advantages vs Disadvantages

- Advantages
    > **(Property 2)** Since a single model is never shown the complete dataset, it’s ability to memorise is significantly constrained. Thus **we can avoid overfitting**(reduce the variance).  
    **(Property 2)** Bagging is most **effective when each sub-model is uncorrelated** by **learning relationships across different components of the data set**.  
    You can extract **prediction intervals**.  
    [(Source) Conor Mc., Why Bagging Works](https://towardsdatascience.com/why-bagging-works-b9961354ee73)

- Disadvantages
    > a loss of **interpretability** of a model  
    computationally **expensive**  
    Bagging reduces the variance while **retaining the bias**.


### (4) Random Forest : a representative bagging model

It builds decision trees on different samples and takes their majority vote for classification and average in case of regression. [(Source) Sruthi E R, Understanding Random Forest](https://www.analyticsvidhya.com/blog/2021/06/understanding-random-forest/)

For not maximally correlated trees **(Property 2)**,  
[(Source) Dr. Robert Kübler, Understanding the Effect of Bagging on Variance and Bias visually](https://towardsdatascience.com/understanding-the-effect-of-bagging-on-variance-and-bias-visually-6131e6ff1385)  
- Use a **random subset of the training samples (bootstrapping)** for each tree. 
- Use a **random subset of features (learning different relationships)** in each step of growing each tree.
- anything else can be added to lower correlation between sub-models.



## 2. Boosting (decrease bias) : Several *sequential* weak learners build a strong learner.  

- (ex) AdaBoost, Gradient Tree Boosting, XGBoost  
(참고 : https://blog.paperspace.com/adaboost-optimizer/)

|![Comparison of bagging and boosting](/docs/MachineLearning/images/bagging_and_boosting.jpeg)|
|:---:|
|Comparison of bagging and boosting [(Source)](https://towardsdatascience.com/ensemble-learning-bagging-boosting-3098079e5422)|

### (1) What is Boosting?

Motivation :  
Humans learn from their mistakes and try not to repeat them futher in life. [(Source)](https://blog.paperspace.com/adaboost-optimizer/)

Central idea :  
implement of *homogeneous ML algorithms* in a **sequential way**, where each of these ML algorithms tries to improve the stability of the model by focusing on the errors made by the previous ML algorithm [(Source)](https://towardsdatascience.com/ensemble-learning-bagging-boosting-3098079e5422)  
**The way of focusing on the predecessor's error** is the key to distinguish between variations of the boosting technique.


### (2) Strong and Weak Learner : Statistical Learning Theory 

[(Source1)](https://www.cs.cornell.edu/courses/cs6781/2020sp/lectures/18-adaboost.pdf)  
[(Source2)](https://www.wisdom.weizmann.ac.il/~ethanf/teaching/ItSLT_16/index.html)

|**Notation**||  
|:---:|:---|
|$\mathcal{X}$ | an input space |
|$\mathcal{Y}$ | an output space |
|$\mathcal{D}$ | and unknown distribution on $\mathcal{X} \times \mathcal{Y}$ |
|$\ell : \mathcal{Y} \times \mathcal{Y} \rightarrow \mathbb{R}$ | a loss function |
|$(x_i, y_i) \in \mathcal{X} \times \mathcal{Y}$ | the *i*-th sample from $\mathcal{D}$|
|$h : \mathcal{X} \rightarrow \mathcal{Y}$ | a hypothesis | 
|$\mathcal{H}$ | *hypothesis class/space/set* : the set of all possible hypothesis |
|$\text{err}_{\mathcal{D}}(h)$| generalization error of $h$ |

Then, in formally notation, 

$$
\text{arg} \min_h L_{\mathcal{D}}(h) = E_{(x,y) \sim \mathcal{D}} \Big[ \ell \big( h(x), y \big) \Big]
$$

is the goal of a machine learning : **find a model $h$ closed to $\mathcal{D}$**

(?) **Definition** *Strong Learnability of $\mathcal{H}$*  
$\mathcal{H}$ is *strongly learnable* if there is an algorithm that  
for $\forall \mathcal{D}$, $\forall \epsilon > 0$, $\forall \delta > 0$, uses $\text{poly} \Big( \dfrac{1}{\epsilon}, \dfrac{1}{\delta}, VC(\mathcal{H}) \Big)$ samples from $\mathcal{D}$ and returns a classifier $h$ such that

$$
\text{Pr} \big( \text{err}_\mathcal{D} (h) \le \epsilon \big) \ge 1 - \delta
$$

The algorithm performing this learning task is call a *strong learner*.

(?) **Definition** *Weak Learnability of $\mathcal{H}$*  
$\mathcal{H}$ is *$\gamma$-weakly learnable* if there is an algorithm that  
for $\forall \mathcal{D}$, $\forall \delta > 0$, uses $\text{poly} \Big( \dfrac{1}{\delta}, VC(\mathcal{H}) \Big)$ samples from $\mathcal{D}$ and returns a classifier $h$ such that

$$
\text{Pr} \big( \text{err}_\mathcal{D} (h) \le \frac{1}{2} - \gamma \big) \ge 1 - \delta
$$

The algorithm performing this learning task is call a *$\gamma$-weak learner*.

(cf)  
![PAC](/docs/MachineLearning/images/PAC.PNG)

Roughly speaking, *Weak Learner* refers to simple models that do only slightly better than random chance. [(Source)](https://medium.com/@toprak.mhmt/gradient-boosting-and-weak-learners-1f93726b6fbd)


### AdaBoost : **Ada**ptive **Boost**ing

- algorithm  
    - AdaBoost makes a **sequence of weak learners** (e.g. decision stumps).  
    - Each weak learner is **made based on weighted samples** from the dataset, and **evaluated its performance** to be used as a weight.
    - When predicting after learning, the prediction follows the **weighted voting/average** of the decisions of each learner.

AdaBoost.M1

1. Let $\lbrace (x_i, y_i) \rbrace_m \in \mathcal{X} \times \mathcal{Y}$ be the dataset with size $m$, where $\mathcal{Y} = \lbrace -1, +1 \rbrace$ (binary classification).  
2. Let $\mathcal{D}_t$ be a distribution such that $\mathcal{D}_t(i)$ is the weight of *i*-th sample $(x_i, y_i)$ at iteration $t$.  
3. Initially, $\mathcal{D}_1(i) \equiv \dfrac{1}{m}$.  
4. For $t = 1, 2, \cdots, T$, where $T$ is the max iteration number,  

$$
\alpha_i = \frac{1}{2} \text{log} \frac{1- \text{TotalError}}{\text{TotalError}}
$$

where $\text{TotalError} = \sum$

### Gradient Tree Boosting

### XGBoost

## 3. Stacking (improve predictions)
- 개별 모델이 예측한 데이터를 다시 training set으로 사용해서 학습  
(참고 : https://lsjsj92.tistory.com/558)