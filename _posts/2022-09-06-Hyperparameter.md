---
layout: post
title: hyperparameter
tags: [DL, Color]
color: brown
author: Ahnho
excerpt_separator: <!--more-->
---

# hyperparameter

: ML에서의 weight, bias 와 같은 주 parameter가 아닌 자동 설정되는 parameter를 의미를 하고 hyperparameter가 잘 설정이 되어있어야 model의 성능이 좋아진다. 

<!--more-->

> - hyperparameter가 설정이 잘못되어 있으면 model의 문제가 없어도 학습이 제대로 되지않는다.
> ex)  사람을 예시로 들어서 학생들이 교육을 받거나 학습을 할때 주변 환경이 좋아야 학습이 더 잘되는거가 있다.
 
--


### Learning rate
- gradient 방향으로 얼마나 움직일지 결정하는것이다.
- 값을 너무 작게 잡으면 학습 속도가 느려지고 local minima문제가 생길수 있다.
- 값을 너무 크게 잡으면 학습 결과가 수렴을 못하고 계속 진동하는 문제가 생긴다.

### momentum
- Gradient desent과정에서 Learning rate만큼 움직이는것이 아니라 momentum을줘서 local minima 문제를 해결하는걸 도와준다
- 여기서 momentum을 준다고 하면 뒤에서 밀어줘서 가속도를 붙여준다고 생각할수 있다.
- global minima에 수렴할수있도록 도와준다.


### Epochs
- 학습을 반복하는 횟수 
- forward ~ backward 까지 1Epoch
- 학습을 많이 한다고해서 꼭 좋은것만 아니다
> - 어느 순간부터 error가 증가할 수있디
> - overfitting의 방지를 위하여 early stopping을 사용해준다.

### Batch Size
- 한번의 배치마다 주는 데이터의 size를 의미
- 한번에 학습하기 힘든 큰데이터나 하드웨어에 부담이 될때 사용한다


### hidden layer 

### weight initialization
- bias는 보통 0으로 초기화
- weight의 초기화는 학습결과에 영향을 크게 끼치기때문에 초기화를할때 주의를 해줘야한다.
- 보통 무작위로 초기화가 이루어지는데 이때 범위는 $$[-l^{-2}, l^{-2}]$$로 이루어 짐.
> 이떼 l은 inpulayer의 있는 유런의 개수를 의미




