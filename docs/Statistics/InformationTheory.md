---
layout : default
title : Information Theory
nav_order : 
math: mathjax3
parent : Statistics
---

# Information Theory
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Definition

### (1) desirable properties

 - 발생가능성과 정보량은 반비례  
    - $P(A) \propto \dfrac{1}{I(A)^{-1}}$
    - $P(B)=1 \implies I(B)=0$
 - 가법성  
    - $A,B:\text{independent} \implies I(A\cap B)=I(A)+I(B)$

### (2) self-information

$$ I(X=x) = - \log P(x) $$

where X : discrete random variable.

### (3) Shannon Entropy $H(P)$

$$ H(P) = H(x) = E_{x \sim P} [I(x)] = E_{x \sim P} [- \log P(x)]$$

$$ H(P) = \sum_x -P(x) \log P(x) $$

where $P$ is a probability distribution of $X$.

### (4) Kullback-Leibler divergence; KLD

$$ D_{KL}(P \Vert Q) = E_{x\sim P} \Big[ \log \frac{P(x)}{Q(x)} \Big] = \sum_x \big[P(x) \log P(x) - P(x)\log Q(x) \big] $$

 - properties : not a metric
    - nonnegative : $ D_{KL}(P \Vert Q) \ge 0 $ (equality holds as $P \equiv Q$) 
    - asymmetric : $D_{KL}(P \Vert Q) \neq D_{KL}(Q \Vert P)$
    - NOT satisfy the triangle inequality 

KLD 는 두 확률분포 $P$, $Q$ 의 차이를 계량화한다.  

### (5) Cross Entropy $H(P,Q)$

$$ H(P,Q) = - E_{x \sim P} [\log Q(x)] = \sum_x -P(x) \log Q(x) $$

*Commonalities* and *differences* with **Shannon Entropy** and **Kullback-Leibler divergence**?


## 2. Cross Entropy $H(P,Q)$ and KLD

$$ D_{KL}(P \Vert Q) = -H(P) + H(P,Q) $$

$$ H(P,Q) = H(P) + D_{KL}(P \Vert Q) $$

Thus,

$$ \min_{Q} H(P,Q) = \min_{Q} D_{KL}(P \Vert Q) $$

$P(x)$ 를 데이터의 true 분포, $Q(x)$ 를 모델이 추정한 데이터의 분포라고 이해한다면,  
비용함수로서의 Cross Entropy 최적화는 추정 분포 $Q(x)$ 를 true 분포 $P(x)$ 와 가깝게 만드는 것으로 볼 수 있다.

## 3. Cross Entropy $H(P,Q)$ and MLE

$$
\begin{align*}
\theta_{ML} &= \mathop{\text{argmax}}\limits_{\theta} P(X;\theta) \\ 
&= \mathop{\text{argmax}}\limits_{\theta} \prod_{i=1}^m P(\mathbf{x}^{(i)};\theta)
\end{align*}
$$

where $\{ \mathbf{x}^{(i)} \}_{1\le i \le m}$ is a set of sample from random distribution $X$.  

For calculation reasons, redefine $\theta_{ML}$ as below (scaled negative log-likelihood):

$$
\begin{align*}
\theta_{ML} &= \frac{1}{m} \mathop{\text{argmin}}\limits_{\theta} -\log P(X;\theta) \\ 
&= \mathop{\text{argmin}}\limits_{\theta} \frac{1}{m} \sum_{i=1}^m -\log P(\mathbf{x}^{(i)};\theta)
\end{align*}
$$

이때, $\dfrac{1}{m}$ 은 $\{ \mathbf{x}^{(i)} \}_{1\le i \le m}$ 의 각 sample 에 대한 empirical distribution $\hat{P}$ 에서의 확률로 이해할 수 있으므로

$$ 
\begin{align*}
\theta_{ML} 
&= \mathop{\text{argmin}}\limits_{\theta} -E_{\hat{P}}[\log P(\mathbf{x};\theta)] \\
&= \mathop{\text{argmin}}\limits_{\theta} H(\hat{P}, P)
\end{align*}
$$

따라서 cross entropy 최적화는 MLE 와 동일하며, 또한 2에 의해 empirical distribution 과 true distribution 을 일치시키려는 과정이다.


## Reference
Deep Learning, Ian Goodfellow
