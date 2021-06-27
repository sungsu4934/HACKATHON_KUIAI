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
  
 
