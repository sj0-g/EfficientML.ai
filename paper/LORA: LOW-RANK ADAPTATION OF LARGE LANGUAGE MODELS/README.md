# 1. Introduction

## 1.1 downstream & upstream

+ downstream
  + 사전 학습된 모델을 활용하여 구체적인 응용 작업을 수행하는 단계입니다.
+ upstream
  + 모델 학습 이전의 단계로, 데이터의 준비나 사전 학습 자체에 해당합니다.

## 1.2 LoRA

+ Problem
  + 미세 조정의 단점은 새로운 모델이 원래 모델과 동일한 수의 파라미터를 갖게 되어, 대규모 모델에서는 저장과 배포가 매우 비효율적이라는 점입니다. 특히 GPT-3와 같은 1750억 개의 트레이너블 파라미터를 가진 모델에서는 큰 문제가 됩니다.

+ Idea
  + 학습된 과대 파라미터 모델에는 사실 내재된 저차원(rank)이 존재한다는 기존 연구 결과를 기반으로 합니다. LoRA는 이 저차원을 활용하여 모델의 적응 시 변경되는 밀집 계층을 효율적으로 최적화합니다.

+ Method
  + 밀집 계층의 변화(파라미터 변경)를 저차원 행렬로 분해하여 학습하는 방법입니다. 이는 사전 학습된 가중치(Pre-trained Weights)는 고정하고, 새로운 작업에서 필요한 적응을 위해 작은 파라미터(행렬 A와 B)만을 학습합니다.

## 1.3 Terminologies

+ $d_{model}$
  
  + Transformer layer의 입력 및 출력 차원의 크기

+ $W_{q}$, $W_{k}$, $W_{v}$, $W_{o}$
  
  + self-attention 모듈에서 쿼리(query), 키(key), 값(value), 출력(output) 프로젝션 행렬을 각각 지칭

+ $r$
  
  + LoRA module의 rank를 지칭

# 2. Problem Statement

기존 Fine Tuning 과정
> <img width="194" alt="image" src="https://github.com/user-attachments/assets/5345f498-f792-434d-8aaa-3e0940084aff">

LoRA
> <img width="233" alt="image" src="https://github.com/user-attachments/assets/9e4a4a0e-d386-4cb2-a512-9ef0b37462dc">

# 3. AREN’T EXISTING SOLUTIONS GOOD ENOUGH

Transformer에 추가되는 Adapter

<img width="486" alt="image" src="https://github.com/user-attachments/assets/f6567de9-06da-487e-a2bb-7f3c251d08f4">



Adapter의 장점

+ 파라미터 효율성
  + 어댑터는 원래 모델의 전체 파라미터에 비해 매우 적은 양의 파라미터만을 추가합니다. 예를 들어, 원래 모델의 1% 미만의 파라미터만을 추가로 학습합니다. 이는 여러 작업에 대해 효율적으로 모델을 미세 조정할 수 있게 합니다.
    
+ 모델 공유의 용이성
  + 어댑터를 사용하면 동일한 사전 학습된 모델을 여러 작업에 적용할 수 있습니다. 각 작업에 필요한 어댑터만 교체하면 되기 때문에, 저장 및 배포가 용이합니다.
 
Adapter의 단점

+ 추론 지연(Inference Latency)
  + 어댑터 레이어는 모델에 추가적인 연산을 요구합니다. 특히, 대규모 신경망에서 어댑터 레이어는 순차적으로 처리되어야 하기 때문에, 모델의 추론 속도가 느려질 수 있습니다. 

+ 프롬프트 튜닝의 어려움
  + 어댑터를 사용하지 않고, 대신 프롬프트를 직접 최적화하는 접근법(프리픽스 튜닝 등)은 또 다른 문제를 야기합니다. 프롬프트 튜닝은 최적화가 어렵고, 학습 가능한 파라미터에 따라 성능이 비선형적으로 변화하는 경향이 있습니다.


