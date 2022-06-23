---
layout : default
title : 04 Decision Tree
nav_order : 4
math: mathjax3
parent : Machine Learning
---

# Decision Tree
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

정확도는 떨어지지만 기초가 되는 알고리즘

## 1. various Indicators of Impurity

### (0) **Notation**

- $D_n$ : dataset of node $n$
    - $D_p, D_j$ : dataset of a parent node and its *j*-th child node
- $N_n$ : the number of samples in a node $n$
    - $N_p, N_j$ : the number of samples in a parent node and its *j*-th child node
- $f$ : feature to use for split
- $I(\cdot)$ : indicator of impurity
- $p(k \vert D_n)$ : frequency of $k$-th class for given dataset $D_n$

### (1) **Definition** *entropy* $I_H$

$$
I_H(D_n) = \sum_{k=1}^K \Big[ - p(k \vert D_n) \cdot \text{log} p(k \vert D_n) \Big]
$$

where $K$ is the number of classes

### (2) **Definition** *Gini impurity* $I_G$

$$
\begin{align*}
    I_G(D_n) 
    &= \sum_{k=1}^K p(k \vert D_n) \big( 1 - p(k \vert D_n) \big) \\
    &= 1 - \sum_{k=1}^K p(k \vert D_n)^2
\end{align*}
$$

어떤 dataset 에서 한 element 를 뽑아 무작위로 label 을 추정할 때 틀릴 확률
    
### (3) **Definition** *classification error* $I_E$

$$
I_E = 1 - \underset{k}{\text{max}} \lbrace p(k \vert D_n) \rbrace
$$

pruning (가지치기) 에 적합한 기준이지만 $p$ 의 변화에 민감하지 않아 tree 생성에는 잘 사용되지 않음.


## 2. Information Gain $IG(\cdot)$

### **Definition** *information gain* $IG(\cdot)$

$$
\begin{align*}
    IG(D_p, f) 
    &= (\text{impurity of parent node}) - (\text{impurity of children nodes}) \\
    &= I(D_p) - \sum_{j=1}^{m} \frac{N_j}{N_p} I(D_j)
\end{align*}
$$


## 3. some algorithms used in Decision Tree

- **ID3** → (extension of D3)
- **C4.5** → (successor of ID3)
- **CART** → (Classification And Regression Tree)
- **CHAID** → (Chi-square automatic interaction detection Performs multi-level splits when computing classification trees)
- **MARS** → (multivariate adaptive regression splines)


## 4. ID3 algorithm
1. It begins with the original dataset $D$ as the *root node*.
2. On each iteration of the algorithm, it iterates through the very unused attribute of the set D and calculates Impurity ($I$) and Information gain ($IG$) of this attribute.
3. It then selects the attribute which has **the smallest Entropy** or **the largest Information gain**.
4. The set $D$ is then split by the selected attribute to produce a subset of the data. (*children nodes*)
5. The algorithm continues to **recur** on each subset, **considering only attributes never selected before**.


## 5. Feature Importance

### **Definition** *node importance* $NI_p$ of a node $p$

$$
\begin{align*}
    NI_p
    &= \frac{N_p}{N_t} I(D_p) - \sum_{j=1}^{m} \frac{N_j}{N_t} I(D_j) \\
    &= \frac{N_p}{N_t} IG(D_p, f)
\end{align*}
$$

where $N_t$ is the number of samples in total dataset


### **Definition** *feature importance* $FI_f$ for a feature $f$
Mean Impurity Decrease

$$
\begin{align*}
FI_f 
&= \frac{\sum\limits_{j\text{: node splits on the feature } f} NI_j}{\sum\limits_{i\text{: all nodes}}NI_i} \\
&= \frac{\sum NI \text{ of the spliting nodes on feature } k}{\sum NI \text{ of all nodes}}
\end{align*}
$$

## Reference
- codeit, 머신러닝 > 결정 트리와 앙상블 기법
- 세바스찬 라시카 외, 머신러닝 교과서 with 파이썬, 사이킷런, 텐서플로 (개정3판), 길벗
- [KD nuggets, "Decision Tree Algorithm, Explained"](https://www.kdnuggets.com/2020/01/decision-tree-algorithm-explained.html)

