# regression-repo-3
**캐나다 차량 별 CO2 배출**

<img src="./asset/canada_car.jfif" width="500px" height="300px" title="px(픽셀) 크기 설정" alt="Canada_Car"></img><br/>

# 1. Intro

## 1-1. Topic
- 차량 모델, 타입, 엔진 크기, co2 배출량 등이 있는 데이터를 활용, 차량의 특성에 따른 CO2 배출량을 회기분석한다.

## 1-2. contents
1. EDA
2. regression
3. 성능평가
4. 추가 데이터 예측

## 1-3. Data-set 
-  이 데이터는 차량의 CO2 배출량이 기능에 따라 어떻게 달라질 수 있는지에 대한 세부 정보를 나타냄 약 7 년 동안의 데이터가 포함되었고
총 7385 개의 행과 12 개의 열이 있음


- ['CO2 Emission by Vehicles'](https://www.kaggle.com/debajyotipodder/co2-emission-by-vehicles?select=CO2+Emissions_Canada.csv) from kaggle
- [캐나다 정부 오픈데이터](https://open.canada.ca/data/en/dataset/98f1a129-f628-4ce4-b24d-6f16bf24dd64#wb-auto-6)에서 추출, 가공
## 1-4. roles

- 김도겸 : 데이터 분석, EDA, 모델링, 성능평가, 회귀분석
- 류승환 : EDA, 매개변수 조사, readme 작성, 회귀분석

# 2. Process 

## 2-1. 데이터 
```
# 데이터 load
df = pd.read_csv('CO2 Emissions_Canada.csv')
df.info()
```

 <img src="./asset/info.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car">

- Make : 브랜드
- Model : 모델 이름
- Vehicle Class : 차량 타입 (Compact, suv, mid-size, two-seater 등)
- Engine Size(L) : 엔진 크기
- Cylinders : 실린더 수
- Transmission : 변속기 타입 (Auto, Auto manual, Auto with select shift 등)
- Fuel Type : 기름 종류 (gasoline, Diesel, Ethanol 등)
- Fuel Consumption City (L/100 km) : 시내에서의 100km 당 기름 소비
- Fuel Consumption Hwy (L/100 km) : 고속도로에서의 100km 당 기름 소비
- Fuel Consumption Comb (L/100 km) : 시내 50, 고속도로 50 비율로 섞은 기름 소비
- Fuel Consumption Comb (mpg) : 연비 (mile per gram)
- **CO2 Emissions(g/km)** : km 당 co2 배출량 (label)

## 2-2. EDA
- CO2 배출량에 대한 histogram

 <img src="./asset/histo.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></
- Heatmap ==> CO2 배출량과의 상관관계 파악

 <img src="./asset/corr.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></
- 생산 회사별 데이터 파악

 <img src="./asset/make.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></

- heatmap에서 봤을 때, 7,8,9번째 해당하는 column과 CO2 배출량과의 관계는 선형적임 따라서 engine size/ cylinder와 co2 배출량과의 관계를 나타낼 수 있음 그 중 cylinder 갯수와 CO2 배출량과의 관계를 생산 회사별로 비교분석하고자 함

## 2-3. Regression
- 총 cylinders와 CO2 배출량의 관계를 rmse로 나타내고 coef(기울기), intercept(y절편)까지 구함

 <img src="./asset/reg1.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></

- 그래프로 나타내고 상위 10개의 회사들도 각각 rmse와 coef, intercept를 구해서 비교하고자 함

 <img src="./asset/reg2.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></

 - 그래프로 표현

<img src="./asset/reg3.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></

- 상위 10개 회사들의 RMSE,COEF, INTERCEPT를 각각 구하여 비교하고 이로 인해, 회사별 CO2 배출량을 비교분석이 가능해짐

<img src="./asset/reg4.png" width="800px" height="500px" title="px(픽셀) 크기 설정" alt="Canada_Car"></


# 3. 성능평가
# 4. REVIEW
1. 2-3에서 첫번째 regression시 cylinders와 Co2 배출량과의 상관관계를 각 회사마다 rmse,coef,intercept를 각각 구해서 비교해봤는데 Engine Size도 같이 넣어서 구해보고, 따로 구해보기도 하면서 각 모델들을 비교해볼 예정
 
>>>>>>> b61a58a43b8325ffb81890eebd5320d96999acfd
