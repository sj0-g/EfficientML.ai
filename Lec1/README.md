# Lecture1 Introduction
[Lecture 1 - Introduction](https://www.youtube.com/watch?v=6cAmS-_vEh8&list=PL80kAHvQbh-pT4lCkDT53zT8DKmhE0idB&index=2)
## 1.1 Model compression

<img width="805" alt="image" src="https://github.com/user-attachments/assets/20dd2e08-3e4a-4d79-bb73-5bdde8724b2d">

Model compression을 통해 성능을 최적화할 수 있습니다.
+ Pruning
  + Pruning은 신경망에서 중요하지 않거나 덜 중요한 연결(가중치)을 제거하여 모델의 크기를 줄이는 방법입니다. 모델이 학습한 후, 특정 연결이 모델의 성능에 거의 영향을 미치지 않는다고 판단되면 이를 제거하여 계산량을 줄이고, 모델을 더 가볍게 만들어 효율성을 높입니다. 
+ Sparcity
  + Sparsity는 신경망의 가중치 중 많은 부분이 0에 가까운 값을 가지는 상태를 말합니다. 희소성을 높이는 것은 모델이 불필요한 가중치를 많이 가지지 않도록 하는 것을 목표로 합니다. 희소한 모델은 메모리 사용을 줄이고, 계산 속도를 높일 수 있습니다.
+ Quantization
  + Quantization은 신경망의 가중치와 활성화를 표현하는 데 사용하는 숫자 비트를 줄여, 모델의 크기와 계산량을 줄이는 기술입니다. 예를 들어, 32비트 부동소수점 대신 8비트 정수로 표현할 수 있습니다. 이렇게 하면 모델의 메모리 요구량과 연산 복잡도를 크게 줄일 수 있습니다.

## 1.2 Zero-shot, One-shot, Few-shot
+ Zero-shot
  + 모델이 학습 과정에서 본 적 없는 새로운 클래스를 인식할 수 있도록 하는 학습 방법입니다. 이는 모델이 클래스 간의 관계나 속성을 통해 일반화하는 능력을 활용합니다.
+ One-shot
  + 각 클래스에 대해 단 하나의 예시만 제공될 때 모델이 그 클래스를 인식할 수 있도록 하는 학습 방법입니다. 이는 유사도 학습이나 메타 학습 등의 기법을 활용하여 구현됩니다.
+ Few-shot
  + 극소량의 데이터만을 이용하여 새로운 작업이나 클래스를 빠르게 학습하도록 설계된 알고리즘을 말합니다. 이 방법은 메타 러닝(meta-learning)이나 학습 전략의 최적화 등을 통해 적은 데이터로도 효과적인 일반화(generalization) 능력을 갖추도록 합니다.
 
## 1.3 Model size and GPU memory

<img width="408" alt="image" src="https://github.com/user-attachments/assets/1b006082-5b25-4fc3-a94c-5938c5ca610c">

+ Transformer (2017): 0.05B (50 million) 파라미터
+ GPT (2018): 0.11B 파라미터
+ BERT (2019): 0.34B 파라미터
+ GPT-2 (2019): 1.5B 파라미터
+ MegatronLM (2019): 8.3B 파라미터
+ GPT-3 (2020): 175B 파라미터
+ T-NLG (2020): 17B 파라미터
+ MT-NLG (2021): 530B 파라미터

## 1.4 BERT model의 Pruning과 Attention Heatmap
### 1.4.1 Pruning

<img width="577" alt="image" src="https://github.com/user-attachments/assets/01eb9f30-8a51-4224-b5cb-bb40e5843629">

+ 원문: "As a visual treat, the film is almost perfect."

  + 처음에 문장은 11개의 토큰과 12개의 어텐션 헤드로 구성된 BERT의 첫 번째 레이어를 통과합니다. 이 단계에서는 100%의 계산과 메모리 접근이 이루어집니다.
  
+ 첫 번째 Pruning 후: "As treat, film perfect."

  + 이 단계에서는 중요하지 않은 단어들("a", "visual", "the", "is", "almost")이 제거되며, 토큰 수가 5개로 줄어듭니다. 어텐션 헤드도 10개로 줄어들며, 전체 계산의 38%만 사용됩니다.
  
+ 두 번째 Pruning 후: "film perfect"

  + 여기서는 "As", "treat"와 같은 덜 중요한 토큰들이 더 제거되고, 최종적으로 2개의 토큰만 남습니다. 어텐션 헤드도 8개로 줄어듭니다. 이 시점에서 전체 계산량의 12%만 사용됩니다.
  
+ 결과: 문장은 "film perfect"라는 핵심적인 정보만 남기고, BERT 모델은 이 문장이 긍정적인 감정을 나타낸다고 분류합니다.

### 1.4.2 Attention Heatmap

+ 이 히트맵에서, 중요하지 않은 토큰들이 단계별로 제거됩니다. 예를 들어, "I", "bet", "the" 등의 토큰이 누적 중요도가 낮다고 판단되면 제거됩니다. 그래프 아래쪽의 텍스트는 "Tokens with small cumulative importance scores are pruned away"라고 되어 있으며, 누적 중요도가 작은 토큰들은 제거된다고 설명하고 있습니다.

