# Dataiku Model Evaluate

- 참고 : https://academy.dataiku.com/path/mlops/production-concepts/1140026

### 1. Dataiku 모델 평가

#### 1-1. Model evaluation store 

- 서로 다른 모델 버전 간에 버전 관리 및 평가를 수행함. 여러 훈련된 후보 모델을 추출하고 배포된 모델과 비교하는데 필요한 데이터를 중앙 집중화하는 구조 역할을 함. Evaluate recipe에서 생성.

- 참고 : https://knowledge.dataiku.com/latest/ml-analytics/model-scoring/concept-model-evaluation-stores.html

  ##### 1-1-1. Evaluate Recipe Input / Output

  - Input : Test Data , Model
  - Output : Output dataset(test Data predict result), Metrics(ex : MAE, MSE, RMSE 등등), Evaluation store

#### 1-2. Online evaluation

- ML 모델의 실시간 예측 성능을 모니터링하고 평가하기 위한 기능. 모델의 예측 결과를 실시간으로 분석하여 모델의 성능을 지속적으로 측정하고 모니터링할 수 있다.

##### 1-2-1. Online evaluation 두 가지 main mode 

- Champion/challenger(shadow testing)
  - 더 나은 모델을 선택하고 현재의 모델을 대체하기 위한 전략적인 결정에 중점을 둠. 기존의 모델과 새로운 모델을 직접 비교하고 선택하는 것을 목표로 함.
- A/B testing
  - 주로 새로운 변화가 기존 모델에 비해 어떤 영향을 미치는지를 검증하고, 통계적으로 유의미한 차이를 확인하는 데 중점을 둠. 일반적으로 성능 개선을 위한 개별 실험으로 간주. Dataiku에서는 챔피언/챌린지가 불가능할때만 사용.

### 2. Model Comparisons

- 여러 모델이나 새로운 모델이 구축 됐을때 모델 성능을 비교하고 성능이 좋은 모델을 배포하기 위해 필요함.
- 
