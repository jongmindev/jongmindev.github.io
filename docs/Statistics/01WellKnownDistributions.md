---
layout : default
title : Well-known Distributions
nav_order : 1
math: mathjax3 
parent : Statistics
---

# Well-known Distributions
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## Discrete Distributions

### summary

| Distribution | pmf / domain | mean | variance | mgf |
|:---:|:---:|:---:|:---:|:---:|
| Bernoulli <br/> $\text{Bernoulli}(p)$ | $p^x q^{1-x}$ <br/> $\small x = 0, 1$ | $p$ | $pq$ | $q+pe^t$ |
| binomial <br/> $B(n,p)$ | $\dbinom{n}{x}p^x q^{n-x}$ <br/> $\small x = 0, 1, \cdots, n$ | $np$ | $npq$ | $(q+pe^t)^n$ |
| hypergeometric <br/> $h(N, M, n)$ <br/> : 비복원추출 | $\dfrac{\dbinom{M}{x}\dbinom{N-M}{n-x}}{\dbinom{N}{n}}$ <br/> $\small x = 0, 1, \cdots, \min \lbrace n,m \rbrace$ | $n \dfrac{M}{N}$ | $n \dfrac{M}{N} \dfrac{N-M}{N} \dfrac{N-n}{N-1}$ | ~~skip~~ |
| geometric <br/> $Geo(p)$ <br/> : 시도 횟수 | $pq^{x-1}$ <br/> $\small x = 1, 2, \cdots$ | $\dfrac{1}{p}$ | $\dfrac{q}{p^2}$ | $\dfrac{pe^t}{1-qe^t}$ |
| negative binomial <br/> $\text{Negbin}(r, p)$ <br/> : $\underset{r}{\bigoplus} Geo(p)$ | $\dbinom{x-1}{r-1} p^r q^{x-r}$ <br/> $\small x = r, r+1, \cdots$ | $r \cdot \dfrac{1}{p}$ | $r \cdot \dfrac{q}{p^2}$ | $(\dfrac{pe^t}{1-qe^t})^r$ |
| Poisson <br/> $\text{Poi}(\lambda)$ | $\dfrac{e^{-\lambda} \lambda^x}{x!}$ <br/> $\small x = 0, 1, \cdots$ | $\lambda$ | $\lambda$ | $e^{\lambda(e^t - 1)}$ |

### relations

![figure]()


## Continuous Distributions

| Distribution | pdf / domain | mean | variance | mgf |
|:---:|:---:|:---:|:---:|:---:|
| uniform <br/> $U(a,b)$ | $\dfrac{1}{b-a}$ <br/> $\small x \in (a,b)$ | $\dfrac{a+b}{2}$ | $\dfrac{(b-a)^2}{12}$ | $\begin{cases} \dfrac{e^{bt} - e^{at}}{(b-a)t} &(t \ne 0) \\ 1 &(t = 0)\end{cases}$ <br/> / <br/> $\dfrac{1}{(b-a)t} \sum\limits_{k=0}^\infty \dfrac{b^k - a^k}{k!} t^k$|
| normal <br/> $N(\mu, \sigma)$ | $\dfrac{1}{\sqrt{2\pi}\sigma} \exp (-\dfrac{1}{2}\left(\dfrac{x-\mu}{\sigma}\right)^2)$ <br/> $\small x \in (-\infty, \infty)$ | $\mu$ | $\sigma$ | $\exp \left( \mu t + \dfrac{1}{2}\sigma^2 t^2 \right)$ |
| exponential <br/> $\exp(\beta)$ <br/> $\small \lambda = \dfrac{1}{\beta}$ | $\begin{aligned} &(1) \dfrac{1}{\beta} e^{-x/\beta} \\ &(2) \lambda e^{-\lambda x} \end{aligned}$ <br/> $\small x \gt 0$ | $\begin{aligned} &(1) \beta \\ &(2) \dfrac{1}{\lambda} \end{aligned}$ | $\begin{aligned} &(1) \beta ^2 \\ &(2) \dfrac{1}{\lambda ^2} \end{aligned}$ | $\begin{aligned} &(1) \dfrac{1}{1-\beta t} \\ &(2) \dfrac{\lambda}{\lambda - t}\end{aligned}$ |
| gamma <br/> $\text{Gamma}(\alpha, \beta)$ <br/> $\small \lambda = \dfrac{1}{\beta}$ | $\dfrac{1}{\Gamma (\alpha) \beta ^\alpha} x^{\alpha - 1} e^{-x/\beta}$ | $\alpha \beta$ | $\alpha \beta ^2$ | $\left( \dfrac{1}{1-\beta t} \right) ^\alpha$ |
| beta <br/> $\text{Beta}(\alpha, \beta)$ | $\dfrac{1}{\Beta(\alpha, \beta)} x^{\alpha -1} (1-x)^{\beta -1}$ <br/> $\small x \in (0, 1)$ | $\dfrac{\alpha}{\alpha + \beta}$ | $\dfrac{\alpha \beta}{(\alpha + \beta + 1)(\alpha + \beta)^2}$ | ~~skip~~ |

### relations

![figure]()
