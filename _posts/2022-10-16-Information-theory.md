---
layout: post
title: Information theory basic for ML
tags: [DL, Color ]
color: brown
author: Ahnho
excerpt_separator: <!--more-->
---

# Information theory  basic for ML

: event가 지닌 정보를 정량화 할 수 있나?

- 기본원리 : 확률이 작을수록 많은 정보를 가진다

<!--more-->

>  즉, 자주 발생하는 사건보다는 잘 일어나지 않는 사건의 정보량이 더 많다.
>  > ex) 아침에 해가 뜬다 vs 아침에 일식이 있었다. 
>  >  : 아침에 해가 뜨는건 매일 발생하는 사건이고 일식은 드문 사건임으로  후자가 더 많은 정보량을 가진다.


## self information 
- 사건 $$e_i$$ 의 정보량 
> : $$h(e_i) =  -\log_2P(e_i)$$ or $$h(e_i) =  -\log_eP(e_i)$$ 
- 해당하는 event가 얼마만큼의 확률을 가지고 있는지
- 확률변수 하나의 대해서 측정 한 것
>ex)
>- 동전에서 앞면이 나오는 사건의 정보량 :  $$-\log_2(\frac{1}{2}) = 1$$
>- 주사위에서 1이 나오는 사건의 정보량  : $$-\log_2(\frac{1}{6}) ≒ 2.58$$

## entropy
- 확률 변수 $$x$$의 불확실성을 나타내는 것
- 전체 사건 정보량을 기대값으로 표현 
- 이산확률 분포 : $$ H(x) = - \sum_{i = 1,k}  P(e_i)\log_2P(e_i)$$  or $$-\sum_{i =1,k} P(e_i)\log_eQ(e_i) $$
- 연속확률분포 : $$ H(x) = - \int_\mathbb{R}  P(x)\log_2P(x)$$ or $$-\int_\mathbb{R} P(x)\log_eQ(x) $$
- 정보를 얼마만큼 보내느냐에 대한 관점
- 확률간의 두 분포를 얼마만큼 유사한지 측정하는 척도로 사용
- 모든 사건이 동일한 확률 -> 어떤 사건이 일어날지 예측이 어려움  -> 불확실성이 큼 -> entropy가 높음 -> 더 큰 정보

## cross entropy
- 두개의 확률 분포가 얼마만큼 정보를 공유하고 있는지의 대한 척도 
 $$ H(P,Q) = - \sum_x P(x)\log_2Q(x) = -\sum_x P(e_i)\log_2Q(e_i) $$
: $$H(P,Q) = - \sum_x P(x)\log_2Q(x) = H(P) + \sum_x P(x)\log_2\frac{P(x)}{Q(x)}$$
- $$\sum_xP(x)\log_2\frac{P(x)}{Q(x)}$$ : KL divergence
> KL divergence :  두 확률분포간의 거리를 계산할때 주로 사용 
- deep learning 의  loss function으로도 많이 사용 
- 데이터  분포 P는 학습 과정에서 변화 X 
- cross entropy를 loss function으로 사용하는 경우 -> KL divergence를 최소화 하는거와 동일하다.

## Reference
- 기계학습(오일석)
- 이재구(인공지능/2022)(국민대)
