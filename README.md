# 고려대학교 해커톤 KUIAI

## 주제: Anomaly Detection in Industrial Environment
 - 좋은 머신러닝 모델을 만들기 위해선 양질의 데이터가 필요
 - 하지만 제조 데이터의 특성상 자동으로 방대한 데이터가 쏟아져 나오기에 라벨링이 어려움
 - 제조 현장의 경우 비정상 데이터가 극히 적기에 라벨링이 성공적으로 진행되었다 해도 데이터 불균형의 문제가 발생. (오류율 1%미만)
 - 딥러닝 기반의 모델은 무거워 학습시간이 오래걸린다. 만약 공장에서 센서위치가 바뀔 경우 재학습이 필요한데, 이 때 빠른학습과 가벼운 모델이어야 서비스가 가능.
 - 활용데이터: https://www.kamp-ai.kr/front/dataset/AiData.jsp
 
## 목표
 - 사출공정 및 용해공정 각각에 대하여 정상 데이터셋만 가지고 학습한 후 비정상 데이터 식별 (Anomaly Detection Using Non-supervised learning)
 - 오류율 최소화 및 학습속도 최소화

## 프로젝트 진행:
 - 1. EDA를 통한 이상치 데이터의 형태 파악
 - 2. 사출공정: AutoEnoder를 활용한 Anomaly Detection
 - 3. 사출공정: Isolationforest를 활용한 Anomaly Detection
 - 4. 용해공정: OneclssSVM을 활용한 Anomaly Detection
 
## 분석결과:
 1. EDA
    - 주어진 데이터에서 비정상 데이터로 식별된 것을 파란색으로, 정상 데이터는 빨간색으로 표시하였다. 시각화로만 보더라고 이상치의 경우 유난히 눈에 띄는 것을 볼 수 있다.
    ![image](https://user-images.githubusercontent.com/28617435/123535143-1342b000-d75d-11eb-9b0d-862619c00cf4.png)
    ![image](https://user-images.githubusercontent.com/28617435/123535148-18076400-d75d-11eb-8068-e6e52ee8a321.png)
# 
 2. 사출공정 Using AutoEncoder
    - AutoEncoder
      > 1) 입력과 출력을 같도록 하는 구조를 의미하는 것으로 노이즈 제거에 탁월한 비지도 머신러닝 방법론
      > 2) input에 최대한 똑같게 output이 나오도록 하는 것으로 노이즈가 없던 부분을 복원하도록 하는 문제를 설계 가능한 장점
    - 결과: Accuracy 30% 대 도출, 매우 저조한 성능과 더불어 예측 시간도 오래걸림
#
 3. 사출공정 Using IsolationForest
    - IsolationForest
      > 1) 데이터 셋을 의사결정나무 형태로 표현해 정상값을 분리하기 위해서는 깊이가 깊고 이상치 값은 의사결정나무 상단부에서 분리된다는 머신러닝 방법론
      > 2) 군집기반 이상탐지 알고리즘에 비해 계산량이 매우 적으며 강건한 모델 생성 가능
    - 결과: Accuracy 98%, F1-SCORE 98% 달성 + 빠른 학습시간(0.45초)
#
 4. 용해공정 Using OneClassSVM
    - OneClassSVM
      > 1) One-class SVM은 novelty detection에 서포트벡터를 사용하는 방법
      > 2) 기존의 서포트 벡터 방식처럼 초평면을 사용하는 것이 아닌 구를 사용하며, 정상 데이터 안에서 데이터 포인트의 밀집도를 찾아 긍정 혹은 부정으로 인식하기 때문에 확률분포가 필요하지 않음
    - 결과: Accuracy 59%, Recall 68% 달성 + 느린 학습시간 (30분)
#
## 총평:
 - Anomaly Detection 분야에 대해 이전에 공부 및 시도를 해본적이 없지만 기존에 많이 쓰이던 RandomForest와 SVM을 변형한 알고리즘과 AutoEncoder라는 방식으로 이상치 탐지가 가능하다는 것에 흥미를 느낌
 - 기존에 지도학습에 관해서만 모델링을 많이 진행했으나 이번에 비지도학습에 대해 배울 수 있던 좋은 기회가 되었음
 - 비록 수상하지는 못했지만, 타 팀의 경우 세 알고리즘을 앙상블하여 성능을 끌어올린 것이 인상깊었음. 이를 토대로 이상치 탐지 뿐만 아니라 앙상블에 대한 학습의 필요성을 느낌
