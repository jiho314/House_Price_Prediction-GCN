# House_Price_Predictor-GCN

***
## Modeling Project E   
Collaborator: 김남훈, 박지호, 이승연, 정건우, 한예림
***

## Overview
서울시 집 값 예측 모델링

### Data
네이버 부동산 서울시 데이터 Crawling
- 서울시 25개구, 구별로 6000개의 부동산, 총 15만개의 집 데이터
- Crawling: nl_crawler.ipynb
- 전처리: preprocess.ipynb
- columns: latitude, longitude, goodsType, payType, floor, contractArea, realArea, direction, tagList, repImgUrl, Deposit, monthlyPay
- targets: Deposit, monthlyPay

위도, 경도 기준 scatter plot:  
<img src="/md_src/data_scatter.png" width="600" height="400" align = 'center'/>


### Crawling
참고링크:
https://github.com/JeeheeMin/land_crawl



### Model
1. Linear Regression & Ensemble

2. GCN Modeling

![모델](/md_src/model_diagram.png)

