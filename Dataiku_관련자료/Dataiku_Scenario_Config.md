# Dataiku Scenario

- 참고 : https://academy.dataiku.com/automation-course-1/668968

### 1. Scenario

- 특정 조건(트리거)이 충족될 때 실행되도록 예약된 작업 집합. 실제 프로젝트가 운영 중일 때 다양한 종류의 Task들을 자동화할 때 유용.
- ex) 정기적으로 새 데이터가 들어오는 경우, 하루 한번 또는 데이터 집합 변경을 탐지할 때마다 Flow를 실행하는 시나리오 생성 가능.
- ex) 모델의 성능 드리프트를 자동으로 감지하여 모델 재교육 가능.
- ex) 로그 정리 또는 클러스터 시작 및 중지와 같은 일부 관리 작업을 자동화할 수 있음.

#### 1-2. Scenario Types

##### 1-2-1. step-based

- 시나리오를 Dataiku의 visual Interface로 구성할 수 있음.

##### 1-2-2. custom Python script

- Python code로 정의 할 수 있음.

#### 1-3. Scenario components

##### 1-3-1. Trigger : 시나리오 실행 트리거

- Time-based trigger : 사용자가 정의한 정기적인 간격으로 시나리오 실행
- Dataset modification trigger : filesystem-based datasets에 사용하는 것으로 데이터 세트에서 변경 사항이 감지될 때마다 사용 (ex : 파일 용량 변화)
- SQL-based dataset trigger : 쿼리를 실행하고 쿼리의 출력이 마지막 실행과 관련하여 변경될 때 시나리오 실행 ex) : SELECT DISTINCT START_TIME FROM TRAFFIC; : START_TIME 이 변경될때 실행
- Python trigger : Python Script로 실행. 사용자가 설정.

##### 1-3-2. Sequence of Steps or Action : 사용자에 의해 구성. 여러 기능 있음.

참고 : https://doc.dataiku.com/dss/latest/scenarios/steps.html (시나리오 step별 기능)

- building or clearing a dataset
- training a model
- running metrics and checks
- refreshing the cache of charts and dashboards
- Writing custom code snippets in Python or SQL
- Managing clusters
- Defining variables at different levels
- Deployment-related actions, and more.

##### 1-3-3. Reporters : 시나리오(성공여부,경고,custom step)에 대해 검증 및 알림 기능

- Mail
- Slack
- Microsoft Teams
- Webhook
- Twilio

#### 1-4. Scenario Config

![scenario_config](.\image\scenario_config.PNG)

- grace delay : 트리거가 감지되고 시나리오가 시작될 때 까지의 시간 간격. ex) 데이터 세트에 새 행을 추가하는 등 변경 사항이 발생하는 동안 트리거 실행 방지.
- Re-check: 변경 사항이 발생하지 않도록 하기 위해 grace delay 후 트리거가 한 번 더 실행. 변경 사항이 발생한 경우 수정이 완료될 때까지 다시 한번 grace delay을 대기함.
