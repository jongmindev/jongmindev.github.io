---
layout : default
title : Markov Process and Expected Value
nav_order : 3
math: mathjax3
has_children : true
---


# 게임 아이템강화(스타포스 시스템) 기대비용의 통계적 도출
{: .no_toc }

Markov Process 를 활용하여
{: .fs-6 .fw-300 }



## Abstract
Markov chain 은 주어진 과거·현재 상태에 대해 미래 상태의 조건부 확률이 현재 상태에만 의존하는 이산 확률 과정을 말한다. 스타포스 시스템은 Nexon 이 서비스하는 mmorpg 게임 Maplestory (이하 메이플스토리) 에서의 아이템강화 시스템을 말한다.  
Markov chain 의 개념을 이용하여 스타포스 시스템에서 아이템을 강화하는 데 드는 비용의 기댓값을 도출한다.  
본 연구에서는 아이템강화의 가장 기본적인 요소만 포함하는 기본모형ⓐ에서부터 메이플스토리 인게임 스타포스 시스템과 동일한 완전모형ⓓ까지 단계적으로 고찰한다.





<!--

#### **Definition** *state value function* $v_i$
$$ v(s) = E[G_t|X_t=s] $$
The state value function $v(s)$ is the expected return starting from state $s$.

#### **Lemma** *Bellman Equation*
$$v(s) = E[g(X_{t+1}) + \gamma v(X_{t+1}) | X_t =s]$$
*proof)* By the definition of return $G_t$ and state value function $v(s)$, it's trivial.

#### **Theorem** *solution for value function*
 $$v(s) = g(s) + \gamma\sum_{s'\in S} p_{ss'}v(s')$$
 where $p_{ss'} = P(X_{t+1}=s'|X_{t}=s)$.

 *proof)* $\sum\limits_{s'\in S} p_{ss'}v(s') = $



#### **Definition** *return* $G_t$
$$ G_t = g(X_{t+1}) + \gamma g(X_{t+2}) + \gamma^2g(X_{t+3}) + \cdots = \sum_{k \ge 1} \gamma^{k-1} g(X_{t+k}) $$
*Return* $G_t$ is the present value of total future reward.

-->
