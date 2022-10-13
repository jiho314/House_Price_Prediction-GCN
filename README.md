# House_Price_Predictor-GCN

## Modeling Project E: 위치 기반 집 값 예측 모델링 
Collaborator: 김남훈, 박지호, 이승연, 정건우, 한예림
***

## Overview
Machine Learning과 Graph Convolutional Network로 네이버 부동산의 집 데이터를 활용해 집 값 예측 모델링을 진행하였다. 집 값에 영향을 주는 조건들을 전부 데이터화하기 어렵기 때문에, 이러한 조건들이 이미 반영된 결과인 주변 집들에 대한 데이터를 활용하고자 하였다. 이에 가장 적합한 모델이 GCN 이라고 판단하여 아래와 같이 모델링하였다.

## 1. Data

    nl_crawler.ipynb: 네이버 부동산, 서울시 집 데이터 Crawling
    preprocess.ipynb: feature 전처리
    
    
- 총 15만개의 집 데이터(서울시 25개구, 구별로 6000개 Crawled)
- columns: latitude, longitude, goodsType, payType, floor, contractArea, realArea, direction, tagList, repImgUrl, Deposit, monthlyPay
- targets: Deposit, monthlyPay
- repo에는 sample 데이터(서대문구)만 첨부

- 데이터 scatter plot(x= 경도, y = 위도):  
<p align = "center">
<img src="/md_src/data_scatter.png" width="450" height="300" align = 'center'/>
</p>


## 2. Crawling

참고링크: https://github.com/JeeheeMin/land_crawl
<p align = "center">
<img src="/md_src/nl_img.png" width="500" height="300" align = 'center'/>
</p>


## 3. Model

### 1) Linear Regression & Ensemble

- monthlyPay 예측 모델 구현
- Linear, RandomForest, GradientBoost, XGBoost, LGBoost Regressor 모델 학습 및 비교
- Prediction example:
<p align = "center">
<img src="/md_src/ml_result.png" width="500" height="300" align = 'center'/>
</p>


### 2) GCN Modeling
#### X
- 집 graph 연결 조건: L1 norm < 0.002 
- graph: 같은 구에서 1000~1400개의 집으로 구성
- 총 12500개의 graph dataset(구별로 500개)
#### Y
- Deposit, monthlyPay


### Model Structure:
![모델](/md_src/model_diagram.png)

#### Loss Result:
<img src="/md_src/GCN_result.png" width="350" height="250" align = 'center'/>

