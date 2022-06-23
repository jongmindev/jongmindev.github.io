---
layout : default
title : 01 Linear Regression
nav_order : 1
math: mathjax3
parent : Machine Learning
---

# Linear Regression
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Multiple Linear Regression

### model

- response variable $y$, responding regressor variables $\lbrace x_i \rbrace _k$
- $y = w_0 + w_1 x_1+ w_2 x_2 + \cdots + w_k x_k + \epsilon$ for each response variable values  
$\epsilon \overset{\text{iid}}{\sim} N(0, \sigma^2)$
- matrix notation :  
$\mathbf{y} = X\mathbf{w} + \mathbf{\epsilon} $  
$\mathbf{\epsilon} \overset{\text{iid}}{\sim} N(\mathbf{0}, \sigma^2 I_n)$

$$
\mathbf{y} = 
\begin{bmatrix}
    y_1 \\
    y_2 \\
    \vdots \\
    y_n
\end{bmatrix},

\quad

X =
\begin{bmatrix}
    1 & x_{11} & x_{12} & \cdots & x_{1k} \\
    1 & x_{21} & x_{22} & \cdots & x_{2k} \\
    \vdots & \vdots & \vdots & \ddots & \vdots \\
    1 & x_{n1} & x_{n2} & \cdots & x_{nk} \\
\end{bmatrix},

\quad

\mathbf{w} = 
\begin{bmatrix}
w_0 \\
w_1 \\
w_2 \\
\vdots \\
w_k
\end{bmatrix},

\quad

\mathbf{\epsilon} = 
\begin{bmatrix}
\epsilon_1 \\
\epsilon_2 \\
\vdots \\
\epsilon_n
\end{bmatrix}
$$

### Least-Square Estimation

$$
\underset{\mathbf{w}}{\text{min}} S(\mathbf{w}) = \sum_i \epsilon_i^2
$$


### normal equation

$$ 
\begin{align*}
    \sum_i \epsilon_i^2 
    &= \mathbf{\epsilon}^T \mathbf{\epsilon} \\
    &= (\mathbf{y} - X\mathbf{w})^T (\mathbf{y} - X\mathbf{w}) \\
    &= \mathbf{y}^T \mathbf{y} - 2\mathbf{y}^T X \mathbf{w} + \mathbf{w}^T X^T X \mathbf{w} \quad (\because \text{scalar})
\end{align*}
$$

Thus, from

$$
\left. \frac{\partial S(\mathbf{w})}{\partial \mathbf{w}} \right\vert _{\hat{\mathbf{w}}} = - 2 X^T \mathbf{y} + 2 X^T X \hat{\mathbf{w}} = 0
$$

we obtain

$$
X^T X \hat{\mathbf{w}} = X^T \mathbf{y}
$$


### gradient descent

$$
\mathcal{L}(\mathbf{w}) = \frac{1}{2k} S(\mathbf{w})
$$

parameter update : $\mathbf{w} \leftarrow \mathbf{w} - \alpha \mathcal{L}^\prime(\mathbf{w}) $ for a learning rate $\alpha$

From 

$$
\begin{align*}
    \mathcal{L}^\prime(\mathbf{w}) 
    &= \frac{1}{k} X^T (X \mathbf{w} - \mathbf{y}) \\
    &= \frac{1}{k} X^T (\hat{\mathbf{y}} - \mathbf{y})
\end{align*}
$$

we obtain

$$
\mathbf{w} 
\leftarrow 
\mathbf{w} - \alpha \cdot \frac{1}{k} X^T (\hat{\mathbf{y}} - \mathbf{y})
$$


## 2. Polynomial Regression

### *k*th-order polynomial regression model in one variable

$$
y = w_0 + w_1 x + w_2 x^2 + \cdots + w_k x^k + \epsilon
$$

### second-order polynomial regression model in two variables

$$
y = w_0 + w_1 x_1 + w_2 x_2 + w_{11} x_1^2 + w_{12} x_1 x_2 + w_{22} x_2^2 + \epsilon
$$

### piecewise linear regression

$$
y = w_0 + w_1 x + w_2 (x-t)_+ + \epsilon
$$

### orthogonal polynomial regression

$$
y = \alpha_0 P_0(x) + \alpha_1 P_1(x) + \cdots + \alpha_k P_k(x) + \epsilon
$$

where $P(x)$ is the *j*th order orthogonal polynomial defined as

$$
\sum_{i=1}^n P_r(x_i)  P_s(x_i) = 0, \quad r \ne s \quad \text{and} \quad P_0(x_i) = 1
$$
