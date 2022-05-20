---
layout : default
title : 02 Revisit to Matrix Multiplication
nav_order : 2
math: mathjax3
parent : Linear Algebra Basic
has_children : true
---

# Revisit to Matrix Multiplication
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. inner product (traditional)

$$
    AB = 
    \begin{pmatrix} 
        \mathbf{a}_{1}^{*} \\ 
        \mathbf{a}_{2}^{*} \\ 
        \mathbf{a}_{2}^{*} 
    \end{pmatrix} 
    \begin{pmatrix} 
        \mathbf{b}_{1} & \mathbf{b}_{2} & \mathbf{b}_{3} 
    \end{pmatrix} = 
    \bigg( \mathbf{a}_{i}^{*} \cdot \mathbf{b}_{j} \bigg)_{i \times j} 
$$


## 2. row operation, column operation

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
    \text{ : row operation (left multiplication)}
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
    \\ \\
    AF &= 
    \begin{pmatrix}
        \mathbf{a}_{1} & \mathbf{a}_{2} & \mathbf{a}_{3}
    \end{pmatrix}
    F
    \text{ : column operaion (right multiplication)}
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


## 3. well-definedness

$$
\begin{align*}
    AB &= 
    A
    \begin{pmatrix} 
        \mathbf{b}_{1} & \mathbf{b}_{2} & \mathbf{b}_{3} 
    \end{pmatrix} = 
    \begin{pmatrix} 
        A\mathbf{b}_{1} & A\mathbf{b}_{2} & A\mathbf{b}_{3} 
    \end{pmatrix}
    \\
    AB &=
    \begin{pmatrix} 
        \mathbf{a}_{1}^{*} \\ 
        \mathbf{a}_{2}^{*} \\ 
        \mathbf{a}_{2}^{*} 
    \end{pmatrix} 
    B = 
    \begin{pmatrix} 
        \mathbf{a}_{1}^{*}B \\ 
        \mathbf{a}_{2}^{*}B \\ 
        \mathbf{a}_{2}^{*}B 
    \end{pmatrix} 
\end{align*}
$$


## 4. outer product

$$
    AB = 
    \begin{pmatrix}
        \mathbf{a}_{1} & \mathbf{a}_{2} & \mathbf{a}_{3}
    \end{pmatrix}
    \begin{pmatrix}
        \mathbf{b}_1^* \\
        \mathbf{b}_2^* \\
        \mathbf{b}_3^*
    \end{pmatrix} 
    =
    \mathbf{a_1}\mathbf{b_1^*} +
    \mathbf{a_2}\mathbf{b_2^*} +
    \mathbf{a_3}\mathbf{b_3^*}
$$

$$A\mathbf{x} =
    \begin{bmatrix}
        \mathbf{a_1} \ \mathbf{a_2} \ \cdots \ \mathbf{a_n}
    \end{bmatrix} 
    \begin{bmatrix}
        x_1 \\
        x_2 \\
        \vdots \\
        x_n
    \end{bmatrix} =
    \mathbf{a_1}x_1 + \mathbf{a_2}x_2 + \cdots + \mathbf{a_n}x_n \in C(A) \\
    \implies \exists \mathbf{x} (A\mathbf{x}=\mathbf{b}) \iff \mathbf{b} \in C(A)
$$

## +5. block multiplication
: exactly same as general multiplication
