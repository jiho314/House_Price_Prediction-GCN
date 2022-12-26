# House_Price_Predictor-GCN

## Modeling Project E: GCN 기반 집 값 예측 모델링 
Collaborator: 김남훈, 박지호, 이승연, 정건우, 한예림
***

## Overview
Graph Convolutional Network로 네이버 부동산의 데이터를 학습하는 집 값 예측 모델링을 진행하였다. 집 값에 영향을 주는 조건들을 전부 데이터화하면 예측이 쉽겠지만 강변, 역세권, 치안 등과 같이 데이터화하기 어려운 조건들이 많다. 타겟의 주변 집 값들은 이러한 조건들이 이미 반영되었다는 점에 집중하였고, 주변의 집 값을 참조하면 이러한 조건을 모두 참조하게 되는 것이라고 판단하였다. 따라서 타겟 집의 정보와 그 주변 집들의 정보(가격포함)를 참조할 수 있도록 GCN layer를 활용하였다.

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

... to be continued ... 
