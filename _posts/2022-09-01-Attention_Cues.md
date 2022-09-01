---
layout: post
title: Attention Cues
tags: [DL, CV, Color, Transformers]
color: brown
author: Ahnho
excerpt_separator: <!--more-->
---

# Attention Cues



: 영장류의 시각 시스템의 시신경은 뇌가 완전히 처리할 수 있는 것보다 훨씬 더 많은 양의 감각 입력을 받는다.( 초당 비트들의 순서로 정보를 수신한다.) 

<!--more-->
하지만 이 자극들이 모두 똑같이 만들어지는 것은 아니다. 의식의 집중은 영장류들이 복잡한 시각 환경에서 먹이, 포식자와 같은 관심있는 물체에 주의를 기울일 수 있게 한다. 이러한 정보를 극히 일부에만 주의를 기울이는 능력은 진화적 의미를 지니고, 인간이 성공 할 수 있게 하였다.(사회화를 위해 자원을 더 현명하게 할당할 수 있게 했다.)

---

##  Attention Cues in Biology

우리의 attention이 시각 세계에 어떻게 배치되는지를 설명하기 위해, 두 가지 구성 요소 프레임 워크가 등장 

1.  *non-nonvolitional cue* 

> : 환경 내 물체의 눈에 띄는 정도에 기초한다.
>
> ex) 밑에 그림을 처럼 5가지 물체가 있고 그중 4가지는 흑백 , 커피는 빨간컵에 담겨 있다고 생각해보자.
>
>  그럼 이 커피는 본질적으로 두드러지고 시각적 환경에서 눈에 띄며, 무의 식적으로 관심을 끌게된다.
>
> ![../_images/eye-coffee.png](https://d2l.ai/_images/eye-coffee.png)

2. *volitional cue*.

>ex) 커피로 카페인을 섭취하게 되면 책을 읽고 싶어진다. 그래서 우리는 고개를 돌려 눈에 초점을 다시 맞춰 밑에 그림처럼 책을 본다. 
>
> :  이 경우는 위에 예시와 달리 커피가 인지능력과 자발적인 통제 하에 책을 선택 하게 되었다.
>
>변수 선택기준에 기반한 volitional cue를 사용하면 이러한 형태의 attention은 더욱 의도적이다.
>
>![../_images/eye-book.png](https://d2l.ai/_images/eye-book.png)

---

## Quries, Keys, and Values

: 위의 내용을 통합하여 attention mechanisms 설계 

- *non-nonvolitional cue* : 간단한 경우를 생각해보면 선택을 편향하기 위해   parameterized 된 fully connected layers 나 non- parameterized 된 max or average pooling 을 간단히 사용할수 있다. 

- 그래서 attention mechanisms 에서 fully connected layer와 pooling layers를 구별하는 것은 *nonvolitional cue* 의 포함이다. 

>  :  volitional cues를 queries라고 부른다.

-  이런  queries가 주어지면 machanisms은 attention pooling을 통해 sensory input(ex) 중간특징 표현)보다 선택을 편향시킨다. 

> : sensory  input 은  attention mechanisms에서 values라고 불린다.

- 일반적으로 모든 values & keys 는 쌍을 이루며 sensory input의 *non-nonvolitional cue* 라고 생각이 할 수 있다.
- 밑에 그림을 보면, 주어진 queries(volitional cue)가 values(sensory input)에 대한 편향 선택을 안내하는 keys(non-volitional cue)와 상호작용할수 있도록 attention pooling을 설게할수 있다.



![../_images/qkv.svg](https://d2l.ai/_images/qkv.svg)

- 위의 메커니즘 설계를 위한 대안은 많이 있다.

> ex) 강화학습을 통한 미분불가능한 attention model 설계 

- queries 와 key 사의 attention weight를 시각화 가능하다.



---

## 참조

- https://d2l.ai/index.html
