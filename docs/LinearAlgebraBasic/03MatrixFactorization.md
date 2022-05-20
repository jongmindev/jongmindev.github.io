---
layout : default
title : 03 Matrix Factorization
nav_order : 3
math: mathjax3 
parent : Linear Algebra Basic
---

# Matrix Factorization (Decomposition)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---


|Factorization<br />Decomposition||meaning|
|:---:|:---:|:---:|
|LU<br />Cholesky|$ A=LU=LDU' $ <br /> $S=A^TA$|only by substitution <br /> → more efficient than LU|
|CR<br />QR|$ A=CR $ <br /> $  A=QR' $|<br />$Q^{-1} = Q^T$ ( $Q^TQ=I$ )|
|Diagonalization|$A = X \Lambda X^{-1} $ <br /> $ S = Q \Lambda Q^T$|power, but inverse <br /> → if symmetric, no inverse (Spectral Theorem)|
|SVD|$A = U \Sigma V^T$|generalized eigenvalue decomposition|


## 1. LU decomposition by Gaussian Elimination

$$ A=LU \rightarrow A=LDU' $$

$L$ : lower triangular matrix with diagonal $\mathbf{1}$.  
$U$ : upper triangular matrix  
$D$ : diagonal matrix = matrix($diag(U)$) : **row operation**($U \rightarrow U'$)  
$U'$ : upper triangular matrix with diagonal $\mathbf{1}$.  

## 1+. Cholesky decomposition (for symmetric)

$$ A=LU=LDU' \rightarrow S=LDL^T=A^TA$$

$S$ : positive definite matrix  
$A$ : upper triangular matrix  
$\phantom{A\text{ :}}$ with independent columns, and diagonal entries are $\sqrt{\text{pivot}}$


## 2-1. CR decomposition

$$A=CR \rightarrow A=QR' $$

$C$ : matrix of independent columns of A(: rectangular)  
$R$ : rref without $\mathbf{0}$ rows. $ = (    I_{\text{rank}(A)}|\mathbf{v}_i  )$
where $C\mathbf{v}_i$ : ith dependent column of $A$  

$$
    \text{ex) }
    A = 
    \begin{bmatrix}
        1 & 3 & 8 \\
        1 & 2 & 6 \\
        0 & 1 & 2
    \end{bmatrix}
    =
    \begin{bmatrix}
        1 & 3 \\
        1 & 2 \\
        0 & 1
    \end{bmatrix}
    \begin{bmatrix}
        1 & 0 & 2 \\
        0 & 1 & 2
    \end{bmatrix}
    = CR
$$


## 2-2. QR decomposition 
: special case of CR decomposition  
$Q$ : orthogonal matrix by Gram-Schmidt ($Q^T Q = I$)  
$R'$ : **column operation**($Q \rightarrow Q'$) $\times R$


## 3-1. Eigenvalue decomposition (Diagonalization)

$$A = X \Lambda X^{-1} \rightarrow S = Q \Lambda Q^T$$

$A$ : square matrix with full independent eigenvectors  
$\Lambda$ : $diag(\text{eigenvalues})$  
$X$ : matrix with corresponding eigenvectors as columns  

## 3-2. on Symmetric matrix $S$
$S$ : symmetric matrix  
$\Lambda$ : $diag(\text{eigenvalues})$  
$Q$ : matrix with corresponding orthonormal eigenvectors as columns  


## 4. Singular Value decomposition (SVD)

$$A = U \Sigma V^T$$

$A$ : rectangular matrix  
$\Sigma$ : singular values  
$U$, $V$ : orthonormal singular vectors  


## 4+. Polar Decomposition

$$ A = U \Sigma V^T = (UV^T)(V\Sigma V^T) = QS $$
$Q$ : orthogonal (rotation)  
$S$ : symmetric (stretching)
