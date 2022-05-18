---
layout : default
title : 10 Rayleigh Quotient
nav_order : 10
math: mathjax3
parent : Linear Algebra Basic
---

# Rayleigh Quotient and Generalized Eigenvalue
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Representative Norms of Matrix about $\sigma_i$
1. $l^2$ norm (Spectral norm) : $\lVert A\rVert_2 = \text{max}\dfrac{\lVert A\mathbf{x}\rVert}{\lVert\mathbf{x}\rVert} = \sigma_1$
2. Frobenius norm : $\lVert A\rVert_F = \sqrt{\sigma_1^2 + \sigma_2^2 + \cdots + \sigma_r^2}$
    - $ \lVert A\rVert_F^2 = \lvert a_{11}\rvert^2 + \lvert a_{12}\rvert^2 + \cdots + \lvert a_{mn}\rvert^2 = \sum_i\sum_j\lvert a_{ij}\rvert^2 $  
     \: another definition

    - $ \lVert A\rVert_F^2 = tr(A^TA) $  
     \: $\lambda(AA^T) = \lambda(A^TA) = \sigma(A)^2 $

    - $ \lVert A\rVert_F^2 = \sigma_1^2 + \sigma_2^2 + \cdots + \sigma_r^2 = \lVert\Sigma\rVert_F^2 $  
     \: $ U, V$ no effect
3. Nuclear norm : $\lVert A\rVert_N = \sigma_1 + \sigma_2 + \cdots + \sigma_r$

- $\lVert Q_1A\rVert = \lVert AQ_2\rVert = \lVert A\rVert $  
$\because Q_1AQ_2 = (Q_1U)\Sigma (V^TQ_2) = (Q_1U)\Sigma (Q_2V)^T$ : same singular values


## 2. Rayleigh Quotient
### (1) Definition

$$ R(S, \mathbf{x}) = \frac{\mathbf{x}^TS\mathbf{x}}{\mathbf{x}^T\mathbf{x}}$$

$S$ : symmetric (like Hermitian) (①all real eigenvalues, ②orthonormal eigenvectors set)  
$\mathbf{x}$ : nonzero

### (2) Properties
- $\max\limits_{\mathbf{x}}R(S, \mathbf{x}) = R(S, \mathbf{q}_1) = \lambda_1$ : the largest eigenvalue  
- $\min\limits_{\mathbf{x}}R(S, \mathbf{x}) = R(S, \mathbf{q}_n) = \lambda_n$ : the smallest eigenvalue
- critical point $\mathbf{x}=\mathbf{q}_k$ of $R(S, \mathbf{x})$, $\implies R(S, \mathbf{q}_k)=\lambda_k$ : corresponding eigenvalue
- $S$ : symmetric $\implies S=A^TA \implies \lambda_1(S)=\sigma_1(A)$ : $\text{maxEV}(S=A^TA) = \text{maxSV}^2(A)$

### (3) Meaning
EV problem of $S$ $\xrightarrow{\text{change}}$ optimization problem of $R(S,\mathbf{x})$


## 3. Generalized Rayleigh Quotient
### (1) Definition

$$ R_M(S, \mathbf{x}) = \frac{\mathbf{x}^TS\mathbf{x}}{\mathbf{x}^TM\mathbf{x}}$$

$S$ : symmetric (like Hermitian) (①all real eigenvalues, ②orthonormal eigenvectors set)  
$M$ : (symmetric) positive definite ($\implies$ invertible)  
$\mathbf{x}$ : nonzero

### (2) Wish

$$
\begin{align*}
    \text{optimization problem of } R_M(S,\mathbf{x}) &\xrightarrow{\text{change}} \text{ EV problem of symmetric } S'  \\
    R_M(S,\mathbf{x}) &\xrightarrow{\text{change}} R_I(S',\mathbf{x}))
\end{align*}
$$

### (3) Solution

$$ R_M(S, \mathbf{x}) = R(H, \mathbf{y}) $$

$ H = M^{-1/2}SM^{-1/2} $ : symetric and similar to $S$  
$ M = Q\Lambda Q^T \implies M^{1/2} = Q\Lambda^{1/2}Q^T \ $ if $\Lambda > 0$  
$ \mathbf{x} = M^{-1/2}\mathbf{y} $


## 4. Generalized Eigenvalue, Eigenvector
### (1) Definition

$$ S\mathbf{x} = \lambda M \mathbf{x} $$

$S$ : symetric  
$M$ : (symetric) positive definite

### (2) Solution

$$ (\lambda, \mathbf{x}) S\mathbf{x}=\lambda M\mathbf{x} \iff (\lambda, \mathbf{y})H\mathbf{y} = \lambda \mathbf{y} $$

$ H = M^{-1/2}SM^{-1/2} $ : symetric and similar to $S$, (positive definite if $S$ is so)  
$ \\{ \mathbf{y}_i \\} $ : orthonormal eigenvectors set  
$ \\{ \mathbf{x}_i \\} = \{ M^{-1/2}\mathbf{y}_i \} $ : $M$-orthogonal eigenvectors set

### (3) Properties
$ \\{\mathbf{x}_i\\} $ : M-orthogonal ($\mathbf{x}_1^T M \mathbf{x}_2=0$)
