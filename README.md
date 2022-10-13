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

데이터 scatter plot(x= 경도, y = 위도):  
<p align = "center">
<img src="/md_src/data_scatter.png" width="600" height="400" align = 'center'/>
</p>


## 2. Crawling

참고링크: https://github.com/JeeheeMin/land_crawl
<p align = "center">
<img src="/md_src/nl_img.png" width="500" height="300" align = 'center'/>
</p>


## 3. Model
1. Linear Regression & Ensemble

2. GCN Modeling

![모델](/md_src/model_diagram.png)

