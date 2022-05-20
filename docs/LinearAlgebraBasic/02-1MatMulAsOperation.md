---
layout : default
title : matmul as a Row/Column Operation
nav_order : 1
math: mathjax3
grand_parent : Linear Algebra Basic
parent: 02 Revisit to Matrix Multiplication

---

# Matrix Multiplication as a Row/Column Operation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Left Multiplication as a Row Operation

$$
\begin{align*}
    EB 
    & = 
    E
    \begin{pmatrix}
        \mathbf{b}_1^* \\
        \mathbf{b}_2^* \\
        \mathbf{b}_3^*
    \end{pmatrix} 
    \\
    & \overset{\text{ex}}{=}
    \begin{pmatrix}
        1 & 0 & 0 \\
        0 & 1 & 0 \\
        -l& 0 & 1
    \end{pmatrix}
    \begin{pmatrix}
        \mathbf{b}_1^* \\
        \mathbf{b}_2^* \\
        \mathbf{b}_3^*
    \end{pmatrix}
    =  
    \begin{pmatrix}
        \mathbf{b}_1^* \\
        \mathbf{b}_2^* \\
        -l\mathbf{b}_1^* + \mathbf{b}_3^*
    \end{pmatrix}
\end{align*}
$$

$$
\begin{align*}
    &\implies \text{rows of } AB \text{ is a linear combination of } B \text{'s rows.} \\
    &\implies \mathbf{v}^*_i \in C(B^T) \text{, where } \mathbf{v}^*_i \text{ is a row vector of } AB
\end{align*}
$$


## 2. Right Multiplication as a Column Operation

$$
\begin{align*}
    AF &= 
    \begin{pmatrix}
        \mathbf{a}_{1} & \mathbf{a}_{2} & \mathbf{a}_{3}
    \end{pmatrix}
    F
    \\
    & \overset{\text{ex}}{=}
    \begin{pmatrix}
        \mathbf{a}_{1} & \mathbf{a}_{2} & \mathbf{a}_{3}
    \end{pmatrix}
    \begin{pmatrix}
        1 & 0 & 0 \\
        0 & 1 & 0 \\
        -l& 0 & 1
    \end{pmatrix}
    =
    \begin{pmatrix}
        \mathbf{a}_{1} - l\mathbf{a}_3 & \mathbf{a}_{2} & \mathbf{a}_{3}
    \end{pmatrix}
\end{align*}
$$

$$
\begin{align*}
    &\implies \text{columns of } AB \text{ is a linear combination of } A \text{'s columns.} \\
    &\implies \mathbf{v}_j \in C(A) \text{, where } \mathbf{v}_j \text{ is a column vector of } AB
\end{align*}
$$
