---
layout : default
title : 06 Eigenvalue, Eigenvector
nav_order : 6
math: mathjax3
parent : Linear Algebra Basic
---

# Eigenvalues and Eigenvectors
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Properties
1. $ \sum \lambda = tr(A) $
2. $ \prod \lambda = det(A) $
3. Symmetric $S$ has **real eigenvalues**, and can choose **orthogonal eigenvectors**.
4. $\lambda_1 \ne \lambda_2 \implies \mathbf{x}_1 \cdot \mathbf{x}_2 = 0$ : different values, independent vectors
5. $\lambda_1 = \lambda_2 \xrightarrow{\text{?}}$ independent vectors (might or might not)
6. $\mathbf{x}_i$ : orthogonal $\iff A^TA=AA^T$ (where $A$ : real)


## 2. Note that
1. (×) $\lambda(A+B) = \lambda(A) + \lambda(B)$ 
2. (×) $\lambda(AB) = \lambda(A) \times \lambda(B)$


## 3. Similar Matrix
: different matrix with **same eigenvalues**  

$$\forall B \text{ : invertible,} \quad BAB^{-1} \text{ is similar to } A$$

$ (BAB^{-1})(B\mathbf{x}) = BA\mathbf{x} = B(\lambda\mathbf{x}) = \lambda(B\mathbf{x}) $ : $\lambda$ is also an eigenvalue of $BAB^{-1}$


## 4. Diagonalization

### (1) Definition

$$ \exists P, D \quad \text{s.t.} \quad P^{-1}AP = D \quad (P \text{ : invertible, } D \text{ : diagonal}) $$

### (2) iff condition
: has a full $n$ independent eigenvectors

### (3) Sketch

$$AX = X\Lambda \rightarrow A = X\Lambda X^{-1}$$

$$
A
\begin{bmatrix} 
    & & \\
    \mathbf{x}_{1} & \cdots & \mathbf{x}_{n} \\
    & & \\
\end{bmatrix}
= 
\begin{bmatrix} 
    & & \\
    A\mathbf{x}_{1} & \cdots & A\mathbf{x}_{n} \\
    & & \\
\end{bmatrix}
=
\begin{bmatrix} 
    & & \\
    \lambda_1\mathbf{x}_{1} & \cdots & \lambda_n\mathbf{x}_{n} \\
    & & \\
\end{bmatrix}
=
\begin{bmatrix} 
    & & \\
    \mathbf{x}_{1} & \cdots & \mathbf{x}_{n} \\
    & & \\
\end{bmatrix}
\begin{bmatrix} 
    \lambda_1 & & \\
    & \ddots & \\
    & & \lambda_n\\
\end{bmatrix}
$$

### (4) Uniqueness
Diagonalization is unique upto  
① permutation (on diagonal $D$)  
② scalar multiplication (on eigenmatrix $X$)
