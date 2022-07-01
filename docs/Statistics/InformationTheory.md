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


### (3) Shannon Entropy $H(P)$ : expected quantity of information

$$ H(P) = H(x) = E_{x \sim P} [I(x)] = E_{x \sim P} [- \log P(x)]$$

$$ H(P) = \sum_x -P(x) \log P(x) $$

where $P$ is a probability distribution of $X$.

{: .quote }
> *(?) It gives a lower bound on the number of bits (if the logarithm is base 2, otherwise the units are different) needed on average to encode symbols drawn from a distribution P. (D)*


### (4) Cross Entropy $H(P,Q)$

$$ H(P,Q) = - E_{x \sim P} [\log Q(x)] = \sum_x -P(x) \log Q(x) $$

{: .quote }
> **Shannon’s source coding theorem**  
*The cross entropy is the expected number of bits needed to compress some data samples drawn from distribution p using a code based on distribution q. (P)*

*Commonalities* and *differences* with **Shannon Entropy** and **Kullback-Leibler divergence**?


### (5) Kullback-Leibler divergence; KLD

$$ 
\begin{align*}
D_{KL}(P \Vert Q) 
&= E_{x\sim P} \Big[ \log \frac{P(x)}{Q(x)} \Big] \\
&= \sum_x \big[P(x) \log P(x) - P(x)\log Q(x) \big] \\
&= -H(P) + H(P, Q)
\end{align*}
$$

{: .quote }
> *The “extra number of bits” you need to pay when compressing data samples from p using the incorrect distribution q as the basis of your coding scheme. (P)*

 - properties : not a metric
    - nonnegative : $ D_{KL}(P \Vert Q) \ge 0 $ (equality holds as $P \equiv Q$) 
    - asymmetric : $D_{KL}(P \Vert Q) \neq D_{KL}(Q \Vert P)$
    - NOT satisfy the triangle inequality 

KLD 는 두 확률분포 $P$, $Q$ 의 차이를 계량화한다.  

{: .quote }
> *(?) In the case of discrete variables, it is the extra amount of information (measured in bits if we use the base 2 logarithm, but in machine learning we usually use nats and the natural logarithm) needed to send a message containing symbols drawn from probability distribution P, when we use a code that was designed to minimize the length of messages drawn from probability distribution Q. (D)*  

{: .quote }
> P 의 방식으로 P 를 압축한 것에 비해, Q 의 방식으로 P 를 압축했을 때 생기는 비효율성?


## 2. Cross Entropy $H(P,Q)$ and KLD

$$ D_{KL}(P \Vert Q) = -H(P) + H(P,Q) $$

$$ H(P,Q) = H(P) + D_{KL}(P \Vert Q) $$

Thus,

$$ \min_{Q} H(P,Q) = \min_{Q} D_{KL}(P \Vert Q) $$

$P(x)$ 를 데이터의 true 분포, $Q(x)$ 를 모델이 추정한 데이터의 분포라고 이해한다면,  
비용함수로서의 Cross Entropy 최적화는 추정 분포(model) $Q(x)$ 를 true 분포(사실은 empirical distribution) $P(x)$ 와 가깝게 만드는 것으로 볼 수 있다.

## 3. Cross Entropy $H(P,Q)$ and MLE

$$
\begin{align*}
\theta_{ML} &= \mathop{\text{argmax}}\limits_{\theta} Q(X;\theta) \\ 
&= \mathop{\text{argmax}}\limits_{\theta} \prod_{i=1}^m Q(\mathbf{x}^{(i)};\theta)
\end{align*}
$$

where $ \lbrace \mathbf{x}^{(i)} \rbrace _{1\le i \le m}$ is a set of sample from random distribution $X$.  

For calculation reasons, redefine $\theta_{ML}$ as below (scaled negative log-likelihood):

$$
\begin{align*}
\theta_{ML} &= \frac{1}{m} \mathop{\text{argmin}}\limits_{\theta} -\log Q(X;\theta) \\ 
&= \mathop{\text{argmin}}\limits_{\theta} \frac{1}{m} \sum_{i=1}^m -\log Q(\mathbf{x}^{(i)};\theta)
\end{align*}
$$

이때, $\dfrac{1}{m}$ 은 $\lbrace \mathbf{x}^{(i)} \rbrace _{1\le i \le m}$ 의 각 sample 에 대한 empirical distribution $P$ (not quite satisfactory representation of the true distribution) 에서의 확률로 이해할 수 있으므로

$$ 
\begin{align*}
\theta_{ML} 
&= \mathop{\text{argmin}}\limits_{\theta} -E_{P}[\log Q(\mathbf{x};\theta)] \\
&= \mathop{\text{argmin}}\limits_{\theta} H(P, Q)
\end{align*}
$$

따라서 cross entropy 최적화는 MLE 와 동일하며,  
[2](#2-cross-entropy-hpq-and-kld)에 의해 model $Q$ 와 empirical distribution $P$ 를 일치시키려는 과정이다.

{: .quote }
> *We want to find the distribution* $Q$ *that is as close as possible to* $P$*. (P)*


## Reference
- (D) Deep Learning, Ian Goodfellow  
- (P) Probability Machine Learning: An Introduction, Christopher Bishop
