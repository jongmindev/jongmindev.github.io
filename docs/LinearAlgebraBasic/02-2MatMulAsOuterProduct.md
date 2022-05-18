---
layout : default
title : matmul as a sum of Outer Product
nav_order : 2
math: mathjax3
grand_parent: Linear Algebra Basic
parent: 02 Revisit to Matrix Multiplication
---

# Matrix Product as a Sum of Outer Product
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---



## 1. Outer Product : rank one matrix

$$ \mathbf{u} \bigotimes_{outer} \mathbf{v} = \mathbf{u} \times \mathbf{v} = \mathbf{u} \mathbf{v}^T \text{ : rank one matrix} $$

row space of $ \mathbf{u} \mathbf{v}^T = C((\mathbf{u} \mathbf{v}^T)^T) \text{ : the line through } \mathbf{v}$ 

cf) inner product : $ \mathbf{u} \cdot \mathbf{v} = <\mathbf{u}, \mathbf{v}> = \mathbf{u}^T \mathbf{v} \text{ : scalar}$  
cf) cross product : $ \mathbf{u} \times \mathbf{v} = \mathbf{u} \bigotimes_{cross} \mathbf{v} \text{ : vector} $


## 2. Matrix Product as a Sum of Outer Product

$$
    AB = 
    \begin{pmatrix}
        \mathbf{a}_{1} & \cdots & \mathbf{a}_{n}
    \end{pmatrix}
    \begin{pmatrix}
        \mathbf{b}_1^* \\
        \vdots \\
        \mathbf{b}_n^*
    \end{pmatrix} 
    =
    \mathbf{a_1}\mathbf{b_1^*} +
    \mathbf{a_2}\mathbf{b_2^*} +
    \cdots + 
    \mathbf{a_n}\mathbf{b_n^*}
    = 
    \sum_i^n \mathbf{a_i}\mathbf{b_i^*}
$$

## 3. total counts

$$ AB = (m \text{ by } n) \text{ times } (n \text{ by } p) $$

- inner product : mp **inner product**, n **multiplications each** : mnp  
- outer product : n **outer product**, mp **multiplications each** : mnp
