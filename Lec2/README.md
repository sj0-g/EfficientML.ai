# Lecture2 Basics of Neural Networks
[Lecture 2 - Basics of Neural Networks, MIT 6.5940, Fall 2023](https://www.youtube.com/watch?v=ieg0RJb7TeI&list=PL80kAHvQbh-pT4lCkDT53zT8DKmhE0idB&index=4)
## 2.1 Fulley Connected Layer

FCL의 모식도

<img width="467" alt="image" src="https://github.com/user-attachments/assets/cae0650c-050f-4b3f-8cb8-5845e71ee830">

+ Input Layer(x)
+ Hidden Layer(y)
+ Output Layer(z)

## 2.2 Activation Functions

활성화 함수

<img width="722" alt="image" src="https://github.com/user-attachments/assets/763de63c-8a36-4adf-a8c7-17dad1c6ddbe">

## 2.3 Convolution

[About Convolution](https://www.youtube.com/watch?v=KuXjwB4LzSA)

+ Convolution의 모식도
  
<img width="696" alt="image" src="https://github.com/user-attachments/assets/8f255520-9ead-4d15-ada3-2d5db742fea7">

+ Convolution의 구성
  + 필터/커널 (Filter/Kernel)
    + 작은 크기의 행렬(예: 3x3, 5x5)로, 입력 데이터와 곱셈을 통해 특징을 추출하는 역할을 합니다.
  + 스트라이드 (Stride)
    + 필터가 입력 데이터를 따라 이동하는 간격을 나타냅니다. 스트라이드가 크면 출력 크기는 작아지고, 작으면 출력 크기는 커집니다.
  + 패딩 (Padding)
    + 필터가 입력 데이터의 경계를 처리할 때 발생하는 출력 크기 축소를 방지하기 위해 입력 데이터의 외곽에 값을 추가하는 방법입니다. (Zero Padding, Reflection Padding, Replication Padding 등이 있습니다.)

+ Convolution의 활용
  + 엣지 검출 (Edge Detection)
    + 필터를 이용해 이미지에서 경계(엣지)를 감지할 수 있습니다.
  + 블러링 (Blurring)
    + 필터를 사용하여 이미지를 흐리게 만들 수 있습니다.
  + 특징 추출 (Feature Extraction)
    + CNN에서 중요한 특징을 추출해 다음 계층으로 전달하여 이미지 분류나 객체 인식에 사용됩니다.

+ Kernel의 의미 

<img width="681" alt="image" src="https://github.com/user-attachments/assets/b096a558-9056-4d4c-9072-8b2d67e34e7e">

## 2.4 Padding

![image](https://github.com/user-attachments/assets/2cf44296-348d-44ec-a7c4-c189b55545de)

+ Zero Padding: 경계를 0으로 채워 넣는 방식.
+ Reflection Padding: 데이터를 경계에서 반사하여 채우는 방식.
+ Replication Padding: 경계의 값을 그대로 복사하여 채우는 방식.

## 2.5 Pooling

<img width="440" alt="image" src="https://github.com/user-attachments/assets/3843eb51-7314-4b83-9d17-a89a7a9cf609">

입력 특징 맵을 다운샘플링하여 더 작은 크기의 출력 특징 맵으로 변환합니다. 이를 통해 중요한 정보는 유지하면서도 데이터의 크기를 줄여 모델의 복잡도를 낮춥니다.

+ Max Pooling은 각 영역에서 가장 큰 값을 선택하여, 중요한 특징을 강조하는 역할을 합니다.
+ Average Pooling은 각 영역의 평균값을 계산하여, 일반적인 특징을 유지하면서 크기를 줄입니다.
+ 풀링 레이어는 학습 중에 업데이트되는 가중치가 없으며, 데이터의 차원을 축소하고 중요한 정보를 압축하는 데 사용됩니다.

## 2.6 Normalization

정규화

> <img width="139" alt="image" src="https://github.com/user-attachments/assets/b9888ae4-26f2-4114-b8ce-5d12a94c1da2">

평균과 표준편차를 구하는 방식

> <img width="150" alt="image" src="https://github.com/user-attachments/assets/926f8107-6ced-453a-8bc0-f9b17cf5abbd">

+ Batch Normalization (배치 정규화)
  + 배치 차원(n)을 기준으로 정규화합니다. 즉, 한 번에 들어오는 여러 샘플(배치)에서의 평균과 표준 편차를 사용하여 정규화합니다.
+ Layer Normalization (레이어 정규화)
  + 레이어 전체의 특징들(c)을 기준으로 정규화합니다. 각 입력 샘플의 특징들을 동일한 분포로 맞춥니다.
+ Instance Normalization (인스턴스 정규화)
  + 각 샘플의 특징 맵(h×w)을 기준으로 정규화합니다. 주로 이미지 스타일 변환과 같은 작업에 사용됩니다.
+ Group Normalization (그룹 정규화)
  + 채널을 그룹으로 나누어 각 그룹에 대해 정규화합니다. 배치 크기에 의존하지 않기 때문에 작은 배치 크기에서도 효과적입니다.

<img width="692" alt="image" src="https://github.com/user-attachments/assets/7ea7f20f-a917-4f93-b533-0a13c98c5053">

## 2.7 h_0

출력 크기를 계산하는 방식

> <img width="145" alt="image" src="https://github.com/user-attachments/assets/68811e52-b0f5-4585-bca4-2629ab5dee1e">

h_i는 입력의 높이, p는 패딩, k_h는 필터의 높이, s는 스트라이드에 해당합니다.

## 2.8 Latency&Throughput

### 2.8.1 Latency

<img width="788" alt="image" src="https://github.com/user-attachments/assets/5c4aae52-d171-4f5a-ba21-309ef586bd32">

### 2.8.2 Throughput

<img width="652" alt="image" src="https://github.com/user-attachments/assets/48794fa7-464c-40b6-ab18-bfb7cd7deb5a">

### 2.8.3 Trade-off in Latency(지연시간) & Throughput(처리량)

<img width="650" alt="image" src="https://github.com/user-attachments/assets/70833041-0328-4540-956a-c2fd051f44c4">

## 2.9 Multiply-Accumulate Operations(MAC)

<img width="782" alt="image" src="https://github.com/user-attachments/assets/8a019ec4-4d34-4ffe-a421-3699577a37ea">

## 2.10 Floating Point Operations (FLOP)

하나의 MAC 연산은 두 개의 FLOP을 포함합니다.
+ 곱셈: b*c
+ 덧셈: a+(b*c)

AlexNet은 총 7억 2400만 개의 MAC 연산을 포함합니다.
+ 총 FLOP 수는 724M * 2 = 1.4G FLOP가 됩니다.

FLOPS는 초당 수행할 수 있는 FLOP의 수를 나타냅니다. 이는 시스템의 성능을 평가하는 지표로 사용됩니다.

## 2.11 Operations (OP)

FLOP (Floating Point Operations)
+ FLOP은 부동 소수점 연산에만 해당하는 연산의 수를 나타냅니다. 즉, 실수 연산(소수점이 포함된 연산)만을 계산합니다.

OP (Operations)
+ OP는 모든 종류의 연산을 포함하는 포괄적인 개념입니다. 여기에는 정수 연산, 부동 소수점 연산, 논리 연산 등 모든 연산이 포함될 수 있습니다.

## 2.12 Model Size

모델 크기는 신경망의 가중치를 저장하는 데 필요한 용량을 의미합니다.

일반적으로 모델 크기를 나타내는 단위는 MB(Megabyte), KB(Kilobyte), 또는 비트(bits)입니다.

모델 사이즈를 계산하는 방법

> <img width="378" alt="image" src="https://github.com/user-attachments/assets/3007124e-1958-4f63-8cc2-e840549e6a0e">

+ AlexNet의 경우 6100만(61M)개의 파라미터를 가지고 있습니다.
+ 만약 모든 가중치가 32비트(4바이트) 숫자로 저장된다면, 전체 저장 용량은 다음과 같습니다.
> <img width="445" alt="image" src="https://github.com/user-attachments/assets/df3379e3-664e-4308-a0ca-2cd2e959b850">
+ 만약 8비트(1바이트) 숫자로 저장된다면, 전체 저장 용량은 다음과 같습니다.
> <img width="269" alt="image" src="https://github.com/user-attachments/assets/01ee0cbb-6dbf-4acf-8d85-6eb4eaaa7e9c">


