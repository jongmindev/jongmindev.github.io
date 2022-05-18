---
layout : default
title : Matrix Calculus
nav_order : 1
parent : Linear Algebra Basic
<!-- last 4 are optional -->
---

# Matrix Calculus (Denominator layout)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 1. Calculus on Manifolds - Differentiation

$$ \overrightarrow{\mathbf{f}} : \mathbf{R}^n \rightarrow \mathbf{R}^m $$
$$ \overrightarrow{\mathbf{x}} \in \mathbf{R}^n : \text{domain}f $$
$$ \frac{\partial \overrightarrow{\mathbf{f}}}{\partial \overrightarrow{\mathbf{x}}} = 
    \begin{bmatrix}
        \vert & & \vert \\
        \frac{\partial f_1}{\partial \overrightarrow{\mathbf{x}}} & \cdots & \frac{\partial f_m}{\partial \overrightarrow{\mathbf{x}}}\\
        \vert & & \vert \\
    \end{bmatrix} 
    \text{ : always based on the denominator vectors}
$$

## 1+. examples

$$ \frac{\partial f}{\partial \overrightarrow{\mathbf{x}}} = 
    \begin{bmatrix}
        \vert \\
        \frac{\partial f}{\partial \overrightarrow{\mathbf{x}}} \\
        \vert \\
    \end{bmatrix} 
    \text{ : } 
    \frac{\partial \text{scalar}}{\partial \text{vector}}
$$

$$ \frac{\partial \overrightarrow{\mathbf{f}}}{\partial x} = 
    \begin{bmatrix}
        \frac{\partial f_1}{\partial x} & \cdots & \frac{\partial f_m}{\partial x}
    \end{bmatrix} 
    \text{ : } 
    \frac{\partial \text{vector}}{\partial \text{scalar}}
$$

$$ \frac{\partial \overrightarrow{\mathbf{f}}}{\partial \overrightarrow{\mathbf{x}}} = 
    \begin{bmatrix}
        \frac{\partial f_1}{\partial x_1} & \frac{\partial f_2}{\partial x_1} & \cdots & \frac{\partial f_m}{\partial x_1} \\
        \frac{\partial f_1}{\partial x_2} & \frac{\partial f_2}{\partial x_2} & \cdots & \frac{\partial f_m}{\partial x_2} \\
        \vdots & \vdots & \ddots & \vdots \\
        \frac{\partial f_1}{\partial x_n} & \frac{\partial f_2}{\partial x_n} & \cdots & \frac{\partial f_m}{\partial x_n} \\
    \end{bmatrix} 
    \text{ : } 
    \frac{\partial \text{vector}}{\partial \text{vector}}
    \text{ (Jacobian)}
$$


## 2. Differentiation Fomulas

Link : [Fomulas - Wiki](https://en.wikipedia.org/wiki/Matrix_calculus#Identities)
