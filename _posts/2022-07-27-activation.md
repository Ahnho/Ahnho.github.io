---
layout: post
title: Dropout
tags: [DL, CV, Color]
color: brown
author: Ahnho
excerpt_separator: <!--more-->
---

# Activation Functions

- 뉴런의 활성화 여부와 weight와 게산을 하고 bias를 추가함을 결정하는 함수
- 입력신호 -> 출력으로 변환 하는 미분 연산자. -> (대부분 비선형성을 추가한다.)

<!--more-->

##  ReLU Function
$$ReLU(x) = max(x,0)$$
- 구현이 단순하고, 다양한 에측 작업에서 우수한 성능으로 인기가 많다.
- 최대값과, 0으로 정의 
- 활성화를 0으로 설정하여 부정적인 요소를 모두 폐기한다. -> 부분 선형 함수

![../_images/output_mlp_76f463_15_0.svg](https://d2l.ai/_images/output_mlp_76f463_15_0.svg)


### ReLU 도함수
- ReLu 함수에서 음수는 도함수가 0, 양수면 1 이다 .
- input이 0이면 미분 불가능하다는 점에 유의해야한다.-> 그래서 input: 0 일때 미분 값을 0으로 말한다. 

![../_images/output_mlp_76f463_27_0.svg](https://d2l.ai/_images/output_mlp_76f463_27_0.svg)

- pReLU : 매개 변수화된 함수를 포함한 변종 : ReLU에 선현 항을 추가해 음수일때도 일부 정보가 전달이 된다.
  :  Dying ReLU Problem
  https://towardsdatascience.com/the-dying-relu-problem-clearly-explained-42d0c54e0d24
$$pLeLU(x) = max(0,x) + \alpha min(0,x)$$

---

## Sigmoid Function
- 입력값을 넣으면 (0,1)까지의 값으로 반환 
- 임계값 미만일때는 0, 초과시는 1을 반환 
- 이진분류에 대해 확률적으로 해석하고자 할때 activation function으로 자주사용된다. 
$$ sigmoid(x) = \prac{1}{1+exp(-x)} $$
- Sigmoid :

![../_images/output_mlp_76f463_39_0.svg](https://d2l.ai/_images/output_mlp_76f463_39_0.svg)

- 하지만 hidden layer에서 훈련하기 쉬운 ReLU로 대체 되었다. 
- sigmoid의 도함수는 입력값이 0일때 최대 값에 도달한다. 
$$ \prac{d}{dx}sigmoid(x) = sigmoid(x)(1-sigmoid(x)) $$
- Sigmoid 도함수

![../_images/output_mlp_76f463_51_0.svg](https://d2l.ai/_images/output_mlp_76f463_51_0.svg)

---

## Tanh Function
- (-1,1)까지의 값을 반환 
- sigmoid처럼 입력값이 0에 가까울 수록 선형변환에 접근한다.
- sigmoid와 모양은 비슷하지만 원점에 대한 점대칭이다. 
$$ tanh(x) = \prac{1-exp(-2x)}{1+exp(-2x)} $$
- Tanh :

![../_images/output_mlp_76f463_63_0.svg](https://d2l.ai/_images/output_mlp_76f463_63_0.svg)

- sigmoid처럼 도함수에서 입력값이 0에 가까워질수록 최대값에 접근한다. 
$$ \prac{d}{dx}tanh(x) = 1-tanh^2(x) $$
- Tanh 도함수 :

![../_images/output_mlp_76f463_75_0.svg](https://d2l.ai/_images/output_mlp_76f463_75_0.svg)

## 참조

- https://d2l.ai/index.html

