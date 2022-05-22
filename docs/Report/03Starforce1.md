---
layout : default
title : Ⅲ Starforce Model ⓑ
nav_order : 3
math: mathjax3 
parent : Markov Process and Expected Value
---

# Ⅲ. 간소화된 스타포스 모형ⓑ : Markov Reward Process
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

메이플스토리 인게임 상의 스타포스는 등급상승, 등급유지, 등급하락, 파괴, 강화단계별 차등 강화비용, 파괴복구(장비흔적 전승), 파괴방지(12성~16성), 각종 이벤트 등 강화확률·강화(시도)비용 변화요소가 모두 존재하는 상당히 복잡한 시스템이다.  
이 모형에서는 이 가운데 ①파괴복구(장비흔적 전승) 비용과 강화확률 변화요소 중 ②찬스타임을 무시한다.  
즉 장비흔적 전승에 있어, 전승받을 장비아이템(소위 노작템)을 구하는데 드는 비용을 0 이라 가정한다. 또, 연속하여 실패하더라도 성공 확률 보정이 없다고 가정한다.


## 1. 문제 제기
장비 파괴 시 복구 비용과 찬스타임을 배제하였을 때, 각 강화 단계에서의 강화비용의 기댓값은 무엇인가.

## 2. Markov Reward Process(MRP)

### **Definition** *reward funtion* $g$

$$ g : S \rightarrow \mathbb{R} $$

(State) Reward $g(s)$ is the constant value that agent is anyway going to receive for being at the state $s \in S$.  
For example, $g(X_i)$ is the reward receive by the agent in the i-th states in the stochastic process.

### **Definition** *Markov Reward Process* $< S, P, g, \gamma>$
$S$ : finite set of states  
$P$ : a transition matrix of given stochastic process with Markov property.  
$g$ : a reward function  
$\gamma$ : a discount factor, $\gamma \in [0, 1]$

## 3. 모델링 - absorbing MRP with zero discount factor
위 정의로부터 간소화된 스타포스 모형ⓑ는 absorbing MRP 에 해당함을 알 수 있다.  
등급상승, 등급유지, 등급하락, 파괴, 파괴방지, 이벤트 등으로 인한 강화확률 변화는 transition matrix 로 모두 표현할 수 있고,  강화단계별 차등 강화비용, 이벤트 등으로 인한 강화(시도)비용 변화는 reward 로 모두 표현할 수 있다.  
이때 discount factor $\gamma = 0$ 이다.

### **Definition** *recurrent state* and $\tau_C$
Let $T_j(1)$ be the first visit time to state $j$.  
A state $i \in S$ is *recurrent* if

$$ P_i[T_i(1)=\infty]=1 $$

where $ P_i(\cdot)=P(\cdot\vert X_0=i) $. Namely, we are sure agent will come back to the state eventually.  
Let $\tau_C$ be the first visit time of the set $C$, then $X_{\tau_C}$ is the value of $X$ at (random) time $\tau_C$.

### **Definition** *expected total reward before absorption* $v_i$

$$ v_i = E_i[\sum_{n=0}^{\tau_C-1}g(X_n)] $$

where $E_i[\cdot] = E[\cdot\vert X_0 = i]$ and $g(i)$ is reward for *visiting* state $i$.

### **Theorem** *solution of expected total reward*

$$ v_i = g(i) + \sum_{k \in T} p_{ik}v_k $$

*proof)* Let $T$ be a set of transient state. Then

$$
\begin{align*}
    v_i 
    &= E_i[\sum_{n=0}^{\tau_C-1}g(X_n)] \\ 
    &= g(i) + E_i[\sum_{n=1}^{\tau_C-1}g(X_n)] \\
    &= g(i) + \sum_{k \in S}E_i[\sum_{n=1}^{\tau_C-1}g(X_n)\vert X_1=k]P_i(X_i=k) \quad \because \text{law of total probability} \\
    &= g(i) + \sum_{k \in S}p_{ik}E_i[\sum_{n=1}^{\tau_C-1}g(X_n)\vert X_1=k] \\
    &= g(i) + \sum_{k \in T}p_{ik}v_k
\end{align*}
$$

since 

$$E_i[\sum\limits_{n=1}^{\tau_C-1}g(X_n)\vert X_1=k] = \begin{cases} E_k[\sum\limits_{n=0}^{\tau_C-1}g(X_n)]=v_k & \quad \text{if } k \in T\\ 0 & \quad \text{if } k \notin T \end{cases}$$

### **Corollary** *expected total reward vector* $\mathbf{v}$
Let $T$ be a set of transient state.  
Let vector $\mathbf{v}=(v_i)$ and $\mathbf{g}=(g_i)$ for $i \in T$. Then

$$ \mathbf{v} = N\mathbf{g} $$

where $N$ is the fundamental matrix.  
*sketch of proof)* By the theorem, $\mathbf{v} = \mathbf{g} + Q\mathbf{v}$. $(I-Q)^{-1} = N$. ▨

위 정리에서는 reward function $g(\cdot)$ 가 state 방문 시 획득하는 reward 를 의미한다.  
하지만 우리의 모형에서 구하고자 하는 강화(시도)비용은 state 를 떠날 때의 reward 에 해당한다.  
그러나 이는 단순 표기의 차이로, expected total reward 의 정의를 위의 $v_i = E_i[\sum\limits_{n=0}^{\tau_C-1}g(X_n)]$ 에서 $ v_i = E_i[\sum\limits_{n=1}^{\tau_C}g(X_n)]$ 로 바꾸고 $g(\cdot)$ 가 state 를 떠날 때 획득하는 reward 를 의미하는 것으로 바꾸어 생각하면 문제없다.

## 4. 3의 결과를 바탕으로 python 을 이용하여 강화비용의 기댓값 도출하기

### (1) 강화 확률표 만들기
GitHub Link : [table.py]()

Output :

### (2) transition matrix $P$ 만들기
GitHub Link : [starforce.py]()

Output :

### (3) vector of reward function value $\mathbf{g}$ 만들기
GitHub Link : [starforce.py]()

Output :

### (4) fundamental matrix $N$ 을 구하여 expected total reward $\mathbf{v}$ 구하기
GitHub Link : [calculator.py]()

Output :

### (5) 반복 simulation 을 통해 얻은 실험적 평균비용과의 비교
GitHub Link : [simulation.py]()

Output :
