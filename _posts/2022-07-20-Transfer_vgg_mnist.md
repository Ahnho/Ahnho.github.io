---
layout: post
title: Transfer learning with VGGNet & MNIST Dataset
tags: [DL, CV, Project , Color]
color: brown
author: Ahnho
excerpt_separator: <!--more-->
---

# Transfer learning with VGGNet & MNIST Dataset

- Goal : vgg16 model로 Tramsfer Learning을 이용하여 MNIST Data 학습시켜 확인해보자
> : 즉, image net을 학습한 model이 MNIST의 숫자 data들을 잘 구별할수있나 확인해보자.

<!--more-->


## Transform & Data set

- VGG16 model은 image-net dataset을 학습을 시킨 모델이라 MNIST data를 바로 사용할수 없어 input size를 변경한다.
> - image net input size: (3,224,224)
> - MINST input size : (1,28,28)

- Resize를 통해 size를 (28 by 28) -> (244 by 244) 변경
-  lmada함수를 통해 1차원인 MNIST data를 3번 쌓아서 3차원으로 채널을 맞춰주었다.
```python3 
trans = transforms.Compose([transforms.ToTensor(),
                            transforms.Normalize((0.1,),(0.5,)),
                            transforms.Resize(224),
                             transforms.Lambda(lambda x: x.repeat(3,1,1))])

# MNIST dataset
train_dataset = MNIST(download_root, transform=trans, train=True, download=True)
test_dataset = MNIST(download_root, transform=trans, train=False, download=True)
```


## DataLoader 작성

```python3
train_dataloader = DataLoader(dataset= train_dataset,
                          batch_size= batch_size,
                          shuffle=True)

val_dataloader = DataLoader(dataset= test_dataset,
                          batch_size= batch_size)

dataloaders_dict = {
    "train": train_dataloader,
    "val": val_dataloader,
}
```

## Network Model

- vgg16 model을 불러오고 classifier의 마지막 부분의 out features를 MNIST Data에 맞게 10으로 변경한다

```python3
net = models.vgg16(pretrained=True)

print(net.classifier)

net.classifier[6] = nn.Linear(in_features=4096, out_features=10)

net = net.to(device)
```

## Loss Function  & optimizer

- Loss Function : CrossEntropyLoss
- optimizer : SGD(lr=0.01, momentum=0.9)

## Training output layer

```python3
params_to_update = []

update_param_names = ["classifier.6.weight", "classifier.6.bias"]

for name, param in net.named_parameters():
    if name in update_param_names:
        param.requires_grad = True
        params_to_update.append(param)
        print(name)
    else:
        param.requires_grad = False
```

## 결과 및 결론

![Image of a glass on a book]({{ "/_portfolio/TLVM.png" | relative_url }})

- 결론 : :: image net을 학습한 vgg16 model로도 MINST의 숫자 Data들을 충분히 높은 정확도로 구별을 할 수 있다!.


- code: [Transfer learning with VGGNet & MNIST Dataset](https://github.com/Ahnho/DeepLeaning_PJ/blob/main/Transfer_Leaning/Transfer_MNIST.ipynb) 
