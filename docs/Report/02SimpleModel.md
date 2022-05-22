---
layout : default
title : Ⅱ Simple Model ⓐ
nav_order : 2
math: mathjax3 
parent : Markov Process and Expected Value
---

# Ⅱ. 단순모형ⓐ : Markov Process
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

마프게임즈의 모바일 게임 ‘게임이 망했다(이하 겜망)’의 장비 아이템 강화 시스템은 ‘①등급상승(성공), ②등급하락(실패), ③등급하락방지’ 의 세 가지 요소만 존재하여 비교적 간단하다.


## 0. '겜망'에서의 장비 강화 시스템에 대한 설명
각 강화단계에서의 강화 성공확률은 아래 표와 같으며, 강화(시도)비용은 인게임 재화인 ‘강화주문서’ 2장이다.  
성공시 강화 등급이 1단계 상승하며, 실패시 (반드시) 강화 등급이 1단계 하락한다.  
강화 시도시에 ‘강화주문서’ 10장으로 자체제작 가능한 ‘축복의 성수’ 아이템을 1개 소모함으로써, 강화 실패시 등급 하락을 방지할 수 있다. 따라서 등급 하락 방지 여부에 따라 강화(시도)비용은 2 또는 12가 된다.

| 강화 단계 | 강화 성공 확률 | 강화 단계 | 강화 성공 확률 | 강화 단계 | 강화 성공 확률 | 강화 단계 | 강화 성공 확률 |
|:---------:|:--------------:|:---------:|:--------------:|:---------:|:--------------:|:---------:|:--------------:|
|   0 → 1   |      100%      |   5 → 6   |       70%      |  10 → 11  |       25%      |  15 → 16  |       12%      |
|   1 → 2   |      100%      |   6 → 7   |       60%      |  11 → 12  |       20%      |  16 → 17  |       10%      |
|   2 → 3   |      100%      |   7 → 8   |       50%      |  12 → 13  |       18%      |  17 → 18  |       8%       |
|   3 → 4   |       90%      |   8 → 9   |       40%      |  13 → 14  |       16%      |  18 → 19  |       6%       |
|   4 → 5   |       80%      |  9 → 10   |       30%      |  14 → 15  |       14%      |  19 → 20  |       4%       |

## 1. 문제 제기
①강화 비용의 기댓값과 ②어느 단계부터 성물을 사용하는 것이 유리한지 탐구한다.  

## 2. Markov chain (Markov Process)

### **Definition**. *Markov property*, *Markov chain* $\{X_1, X_2, \cdots\}$
Series of random variables (Stochastic Process) $\{X_1, X_2, \cdots\}$ is a *Markov chain* if  

$$\forall t, \mathbf{P}(X_{t+1}|X_1, X_2, \cdots, X_t) = \mathbf{P}(X_{t+1}|X_t)$$

The above equation is called the *Markov property*.

> “The future is independent of the past given the present”

### **Definition** *state*, *step*
A *state* is the current situation of the agent. The *set $S$ of states* is a codomain of each $X_i$.  
A *step* is each transition from one state to another state.

### **Definition** *absorbing state*, *transient state*, *absorbing Markov chain*
An *absorbing state* is a state that is impossible to leave once reached.  
A *transient state* is a state that is not absorbing.  
An *absorbing Markov chain* is a Markov chain of which every state can reach an absorbing state (in single or multiple steps).

강화 성공 확률은 오로지 현재 강화 단계에 의해서만 결정된다. 따라서 이상의 정의로부터 단순모형ⓐ는 absorbing Markov Process 임을 알 수 있다. 

## 3. 모델링 - absorbing Markov Process

### **Definition** *transition matrix* $P=(p_{ij})$
The transition matrix $P=(p_{ij})$ of the Markov chain $\{X_1, X_2, \cdots\}$ is a matrix such that

$$ p_{ij} = P(X_j|X_i)$$

### **Definition** *fundamental matrix* $N$ for given transition matrix $P$
Let $Q$ be the sub-matrix of $P$ without row and columns of any absorbing states.  
Namely, for example, $ P = \begin{bmatrix} Q & R\\ \mathbf{0} & \mathbf{1} \end{bmatrix}$. $\mathbf{1}$ is a diagonal matrix with diagonal elements $1$.  
(Note that the last rows $\begin{bmatrix} \mathbf{0} & 1 \end{bmatrix}$ implies that right-bottom diagonals are absorbing states.)  
Then the *fundamental matrix* $N$ is defined as 

$$N=(I-Q)^{-1}$$

### **Definition** *n-step transition probability* $p_{i,j}^{(n)}$, *n-step transition probability matrix* $P_{i,j}^{(n)}$ for a Markov chain

$$p_{i,j}^{(n)} = P(X_{k+n}=j|X_k=i)$$

$$P^{(n)} = (p_{i,j}^{(n)})$$

### **Theorem** *Chapman-Kolmogorov Equation*

$$p_{i,j}^{(n)} = \sum_{k, 0 \le m \le n} p_{i,k}^{(m)}p_{k,j}^{(n-m)}$$

for integer $m$.  
*proof)* Trivial. ▨

### **Theorem** $P^{(n)} = P^n$
*proof)* $P^{(1)} = P^1$ and $P^{(n+1)} = P^nP$ by Chapman-Kolmogorov Equation and the definition of matrix multiplication. Mathematical induction. ▨

### **Theorem** *expected number of visits*
The expected number of visits (including the initial state) from transient state $i$ to transient state $j$ is same as $n_{ij}$ for fundamental matrix $N=(n_{ij})$.  
*sketch of proof)* Considering $P^{(n)} = P^n$, each entry $q_{ij}^{(n)}$ of $Q^n=(q_{ij}^{(n)})$ is the probability of *n-step* transition *before absorbing* from state $i$ to state $j$. Since $Q^n \rightarrow 0$, $(I-Q)^{-1} = I + Q + Q^2 + \cdots$. By the definition of expected value of random variables, done. ▨


## 4. 3의 결론을 바탕으로 python 을 이용하여 강화비용의 기댓값 도출하기

### (1) transition matrix $P$ 만들기
GitHub Link : [gamemang.py]()  

Output 1 (성수 - 실패시 하락 방지 사용하지 않는 경우) : 
```console
>>> (gamemang_transition_matrix_class.transition_matrix * 100).astype(int)
[[  0 100   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0 100   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0 100   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0  10   0  90   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0  20   0  80   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0  30   0  70   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0  40   0  60   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0  50   0  50   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0  60   0  40   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0  70   0  30   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0  75   0  25   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0  80   0  20   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0  82   0  18   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0  84   0  16   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0  86   0  14   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0  88   0  12   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  90   0  10   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  92   0   8   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  94   0   6   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  96   0   4]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 100]]
```

Output 2 (성수 - 실패시 하락 방지 사용하는 경우) : 
```console
>>> (GameMangTransitionMatrix(20, True).transition_matrix * 100).astype(int)
[[  0 100   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0 100   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0 100   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0  10  90   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0  20  80   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0  30  70   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0  40  60   0   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0  50  50   0   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0  60  40   0   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0  70  30   0   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0  75  25   0   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0  80  20   0   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0  82  18   0   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0  84  16   0   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0  86  14   0   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  88  12   0   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  90  10   0   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  92   8   0   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  94   6   0]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  96   4]
 [  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 100]]
```

### (2) 기댓값 도출하기
GitHub Link : [calculator.py]()  

Output :
```console
>>> GameMangCalculator(goal=20).print_interval_cost()
              no water  yes water no is better  profit
from                                                  
0                 1.00       1.00          NaN     NaN
1                 1.00       1.00          NaN     NaN
2                 1.00       1.00          NaN     NaN
3                 1.22      11.11         True    9.89
4                 1.56      12.50         True   10.94
5                 2.10      14.29         True   12.19
6                 3.06      16.67         True   13.60
7                 5.06      20.00         True   14.94
8                10.10      25.00         True   14.90
9                26.89      33.33         True    6.44
10               84.67      40.00        False     NaN
11              343.67      50.00        False     NaN
12            1,571.15      55.56        False     NaN
13            8,254.78      62.50        False     NaN
14           50,715.06      71.43        False     NaN
15          371,918.78      83.33        False     NaN
16        3,347,279.02     100.00        False     NaN
17       38,493,721.23     125.00        False     NaN
18      603,068,315.93     166.67        False     NaN
19   14,473,639,607.40     250.00        False     NaN
```
각 행은 index 에 해당하는 강화 단계에서 그 다음 강화 단계를 달성하기 위한 강화 비용에 관한 정보를 담고 있다.  
첫 번째 열 'no water' 는 성수(하락방지) 미사용시 기대 강화비용이다.  
두 번째 열 'yes water' 는 성수(하락방지) 사용시 기대 강화비용이다. (0단계 ~ 2단계에서는 성수사용이 불가능함)  
세 번째 열 'is better' 는 성수 사용를 사용하지 않는 것이 유리한지(성수 사용이 불리한지) 여부이다.  
네 번째 열 'profit' 은 성수 사용이 불리한 경우에, 기대비용상 그 불리한 정도를 나타낸다.

### (3) 문제의 해결 : 어느 단계부터 성수를 사용하는 것이 유리한지
강화 성공 확률이 100% 여서 성수 사용이 불가능한 (그리고 불필요한) 0단계 ~ 2단계를 제외하면, 10단계에서부터야 비로소 성수를 사용하는 것이 기대 강화 비용상 유리하다.  
따라서 **9단계 → 10단계 강화까지는 성수를 사용하지 않고, 그 이후부터 성수를 사용하는 것이 기대 강화비용상 최적**이다.  
다만, 현실적으로는 9단계 → 10단계 강화에서 성수 미사용의 비용 이익이 6.44에 불과하고 이 때의 성공확률이 30%로서 강화 비용의 분산이 상당히 클 것임을 감안한다면, 약간의 기대 비용상 손해를 감수하고 성수를 사용하여 강화하는 것도 충분히 합리적인 선택이라고 볼 수 있다.
