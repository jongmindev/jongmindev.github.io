---
layout : default
title : 01Regression
nav_order : 1
math: mathjax3
parent : Machine Learning
---

# Regression
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Linear Regression

### model

- response variable $y$, responding regressor variables $\{x_i\}_k$
- $y = \theta_0 + \theta_1 x_1+ \theta_2 x_2 + \cdots + \theta_k x_k + \epsilon$ for each response variable values  
$\epsilon \overset{\text{iid}}{\sim} N(0, \sigma^2)$
- matrix notation :  
$\mathbf{y} = X\mathbf{\theta} + \mathbf{\epsilon} $  
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

\mathbf{\theta} = 
\begin{bmatrix}
\theta_0 \\
\theta_1 \\
\theta_2 \\
\vdots \\
\theta_k
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
\underset{\mathbf{\theta}}{\text{min}} S(\mathbf{\theta}) = \sum_i \epsilon_i^2
$$


### normal equation

$$ 
\begin{align*}
    \sum_i \epsilon_i^2 
    &= \mathbf{\epsilon}^T \mathbf{\epsilon} \\
    &= (\mathbf{y} - X\mathbf{\theta})^T (\mathbf{y} - X\mathbf{\theta}) \\
    &= \mathbf{y}^T \mathbf{y} - 2\mathbf{y}^T X \mathbf{\theta} + \mathbf{\theta}^T X^T X \mathbf{\theta} \quad (\because \text{scalar})
\end{align*}
$$

Thus, from

$$
\left. \frac{\partial S(\mathbf{\theta})}{\partial \mathbf{\theta}} \right\vert _{\hat{\mathbf{\theta}}} = - 2 X^T \mathbf{y} + 2 X^T X \hat{\mathbf{\theta}} = 0
$$

we obtain

$$
X^T X \hat{\mathbf{\theta}} = X^T \mathbf{y}
$$


### gradient descent

$$
L(\mathbf{\theta}) = \frac{1}{2k} S(\mathbf{\theta})
$$

parameter update : $\mathbf{\theta}_{i+1} = \mathbf{\theta}_i - \alpha L^\prime(\mathbf{\theta}) $ for a learning rate $\alpha$

From 

$$ 
L^\prime(\mathbf{\theta}) = \dfrac{1}{k} X^T (X \mathbf{\theta} - \mathbf{y}) $$

we obtain

$$
\mathbf{\theta} 
\leftarrow 
\mathbf{\theta} - \alpha \cdot \frac{1}{k} X^T (X \mathbf{\theta} - \mathbf{y})
$$


## 2. Polynomial Regression

### *k*th-order polynomial regression model in one variable

$$
y = \theta_0 + \theta_1 x + \theta_2 x^2 + \cdots + \theta_k x^k + \epsilon
$$

### second-order polynomial regression model in two variables

$$
y = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + \theta_{11} x_1^2 + \theta_{12} x_1 x_2 + \theta_{22} x_2^2 + \epsilon
$$

### piecewise linear regression

$$
y = \theta_0 + \theta_1 x + \theta_2 (x-t)_+ + \epsilon
$$

### orthogonal polynomial regression

$$
y = \alpha_0 P_0(x) + \alpha_1 P_1(x) + \cdots + \alpha_k P_k(x) + \epsilon
$$

where $P(x)$ is the *j*th order orthogonal polynomial defined as

$$
\sum_{i=1}^n P_r(x_i)  P_s(x_i) = 0, \quad r \ne s \quad \text{and} \quad P_0(x_i) = 1
$$
