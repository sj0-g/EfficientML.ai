# Lecture2 Basics of Neural Networks
[Lecture 2 - Basics of Neural Networks, MIT 6.5940, Fall 2023](https://www.youtube.com/watch?v=ieg0RJb7TeI&list=PL80kAHvQbh-pT4lCkDT53zT8DKmhE0idB&index=4)
## 2.1 Fulley Connected Layer

<img width="467" alt="image" src="https://github.com/user-attachments/assets/cae0650c-050f-4b3f-8cb8-5845e71ee830">

+ Input Layer(x)
+ Hidden Layer(y)
+ Output Layer(z)

## 2.2 Activation Functions

<img width="722" alt="image" src="https://github.com/user-attachments/assets/763de63c-8a36-4adf-a8c7-17dad1c6ddbe">

## 2.3 Convolution

[About Convolution](https://www.youtube.com/watch?v=KuXjwB4LzSA)

+ Convolution의 모식도
  
<img width="696" alt="image" src="https://github.com/user-attachments/assets/8f255520-9ead-4d15-ada3-2d5db742fea7">

+ Convolution의 구성
++ 필터/커널 (Filter/Kernel)
+++ 작은 크기의 행렬(예: 3x3, 5x5)로, 입력 데이터와 곱셈을 통해 특징을 추출하는 역할을 합니다.
++ 스트라이드 (Stride)
+++ 필터가 입력 데이터를 따라 이동하는 간격을 나타냅니다. 스트라이드가 크면 출력 크기는 작아지고, 작으면 출력 크기는 커집니다.
++ 패딩 (Padding)
+++ 필터가 입력 데이터의 경계를 처리할 때 발생하는 출력 크기 축소를 방지하기 위해 입력 데이터의 외곽에 값을 추가하는 방법입니다. (Zero Padding, Reflection Padding, Replication Padding 등이 있습니다.)

+ Convolution의 활용
++ 엣지 검출 (Edge Detection)
+++ 필터를 이용해 이미지에서 경계(엣지)를 감지할 수 있습니다.
++ 블러링 (Blurring)
+++ 필터를 사용하여 이미지를 흐리게 만들 수 있습니다.
++ 특징 추출 (Feature Extraction)
+++ CNN에서 중요한 특징을 추출해 다음 계층으로 전달하여 이미지 분류나 객체 인식에 사용됩니다.

+ Kernel의 의미 

<img width="681" alt="image" src="https://github.com/user-attachments/assets/b096a558-9056-4d4c-9072-8b2d67e34e7e">

## 2.4 Padding

![image](https://github.com/user-attachments/assets/2cf44296-348d-44ec-a7c4-c189b55545de)

+ Zero Padding: 경계를 0으로 채워 넣는 방식.
+ Reflection Padding: 데이터를 경계에서 반사하여 채우는 방식.
+ Replication Padding: 경계의 값을 그대로 복사하여 채우는 방식.


