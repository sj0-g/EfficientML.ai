# Lec1 Introduction
## Model compression
<img width="805" alt="image" src="https://github.com/user-attachments/assets/20dd2e08-3e4a-4d79-bb73-5bdde8724b2d">

Model compression을 통해 성능을 최적화할 수 있다. 
+ Pruning
+ Sparcity
+ Quantization

## Zero-shot, One-shot, Few-shot
+ Zero-shot
  + 모델이 학습 과정에서 본 적 없는 새로운 클래스를 인식할 수 있도록 하는 학습 방법입니다. 이는 모델이 클래스 간의 관계나 속성을 통해 일반화하는 능력을 활용합니다.
+ One-shot
  + 각 클래스에 대해 단 하나의 예시만 제공될 때 모델이 그 클래스를 인식할 수 있도록 하는 학습 방법입니다. 이는 유사도 학습이나 메타 학습 등의 기법을 활용하여 구현됩니다.
+ Few-shot
  + 극소량의 데이터만을 이용하여 새로운 작업이나 클래스를 빠르게 학습하도록 설계된 알고리즘을 말합니다. 이 방법은 메타 러닝(meta-learning)이나 학습 전략의 최적화 등을 통해 적은 데이터로도 효과적인 일반화(generalization) 능력을 갖추도록 합니다.
