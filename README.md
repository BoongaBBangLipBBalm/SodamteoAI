# 🌱소담터: 아름답고 정성스러운 농작물 관리 스마트 터전 AI Repository
## 프로젝트 소개
- IoT 디바이스와 산업 플랫폼을 연동하여 자동화하는 트렌드에 따라 농업 자동화 플랫폼 개발에 기여
- 농수산물의 유통을 보다 용이하게 하고, 농업 직군으로의 유입을 목적으로 함
- [SodamteoBack](https://github.com/BoongaBBangLipBBalm/SodamteoBack)에서 사용하기 위한 AI 연구 레포지토리

### 폴더 구조
```bash
./
├── CropPricePrediction/ # 작물 시가 예측
│   ├── RicePricePrediction.ipynb
│   ├── Rice_Price_answer.csv
│   ├── Rice_Price_data.csv
│   └── ckpt/
├── CropSelection/ # 작물 선택
│   ├── Crop_Selection.ipynb
│   ├── Crop_recommendation.csv
│   └── Linear_Regression_Crop_Selection.pkl
├── README.md
├── RiceLeafDiseaseClassification/ # 작물 질병 진단
│   ├── Rice_Disease_Classification.ipynb
│   ├── YOLOv8n-cls_Rice_Disease.pt
│   └── data_rice_disease/
└── requirements.txt
```

### 실행 방법
**실행 환경**: Python 3.10
```bash
git clone https://github.com/BoongaBBangLipBBalm/SodamteoAI.git
cd SodamteoAI
pip install -r requirements.txt
# 각 디렉토리로 이동 후 jupyter notebook 실행
```

## 수행 내용
### 📈 작물 시가 예측
**개요**  
- 한국의 기후와 작물의 시가 사이에 존재하는 관계를 파악
- 해당 관계를 바탕으로 다변량 예측 모델 NHITS를 사용하여 향후 3개월의 쌀 20kg 중도매가 예측

|구분|설명|
|---|---|
|모델|Neuralforecast 라이브러리의 다변량 시계열 예측 NHITS 모델|
|데이터|[한국농수산식품유통공사 KAMIS](https://www.kamis.or.kr/customer/price/wholesale/period.do)의 월별 쌀 중도매인 판매 가격 데이터 <br> [기상청](https://data.kma.go.kr/stcs/grnd/grndRnList.do)의 월별 기온, 강수량, 기압, 습도, 풍속, 일사/일조량 데이터|

**결과**  
- 7월부터 3개월 간의 예측 결과 MAE(Mean Absolute Error, 평균 절대 오차) 약 797원 달성

### 🌾 작물 선택
**개요**  
- 온습도, 토양 영양 정보 등을 기반으로 재배하기 적절한 작물을 선택하는 모델
- 주변 환경과 작물의 요인의 관계에 선형 관계가 보장되며, Regression 형태의 문제로 해결

|구분|설명|
|---|---|
|모델|Linear Regression|
|데이터|[Kaggle의 Smart Farming Optimizing Engine](https://www.kaggle.com/code/chitrakumari25/smart-farming-optimizing-engine/notebook)|

**결과**  
- test dataset에 대해 Accuracy 0.9545 달성

### 💉 작물 질병 진단
**개요**  
- 벼의 질병을 Bacterialblight, Blast, Brownspot, Tungro로 구분하여 각각에 대한 이미지 입력 시 classification 결과 출력
- 작물의 질병을 보다 손쉽게 파악하여 발빠른 대처를 위한 기반을 마련

|구분|설명|
|---|---|
|모델|YOLOv8-nano의 classification 버전|
|데이터|[Kaggle의 Rice Leaf Disease Images](https://www.kaggle.com/datasets/nirmalsankalana/rice-leaf-disease-image?select=Tungro)|

**결과**  
- Accuracy 1.0 달성
