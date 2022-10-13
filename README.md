# House_Price_Predictor-GCN

***
## Modeling Project E   
Collaborator: 김남훈, 박지호, 이승연, 정건우, 한예림
***

## Overview
서울시 집 값 예측 모델링

## 1. Data

    nl_crawler.ipynb: 네이버 부동산, 서울시 집 데이터 Crawling
    preprocess.ipynb: feature 전처리
    
    
- 총 15만개의 집 데이터(서울시 25개구, 구별로 6000개 Crawled)
- columns: latitude, longitude, goodsType, payType, floor, contractArea, realArea, direction, tagList, repImgUrl, Deposit, monthlyPay
- targets: Deposit, monthlyPay
- repo에는 sample 데이터(서대문구)만 첨부

- 데이터 scatter plot(x= 경도, y = 위도):  
<p align = "center">
<img src="/md_src/data_scatter.png" width="600" height="400" align = 'center'/>
</p>


## 2. Crawling

참고링크: https://github.com/JeeheeMin/land_crawl
<p align = "center">
<img src="/md_src/nl_img.png" width="500" height="300" align = 'center'/>
</p>


## 3. Model

### 1) Linear Regression & Ensemble

- Linear, RandomForest, GradientBoost, XGBoost, LGBoost Regressor 모델 학습 및 비교
- monthlyPay 예측
- Prediction example:
<p align = "center">
<img src="/md_src/ml_result.png" width="500" height="300" align = 'center'/>
</p>


### 2) GCN Modeling
#### X:
- 집 graph 연결 조건: L1 norm < 0.002 
- graph: 같은 구에서 1000~1400개의 집으로 구성
- 총 12500개의 graph dataset(구별로 500개)
#### Y:
- Deposit, monthlyPay


### Model Structure:
![모델](/md_src/model_diagram.png)

#### Result:
<p align = "center">
<img src="/md_src/gcn_result.png" width="500" height="300" align = 'center'/>
</p>
