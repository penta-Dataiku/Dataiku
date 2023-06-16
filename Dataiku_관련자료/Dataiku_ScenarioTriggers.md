# Dataiku Scenario

- 참고 : https://academy.dataiku.com/automation-course-1/668968

### 1. Scenario

- 특정 조건(트리거)이 충족될 때 실행되도록 예약된 작업 집합. 실제 프로젝트가 운영 중일 때 다양한 종류의 Task들을 자동화할 때 유용.
- ex) 정기적으로 새 데이터가 들어오는 경우, 하루 한번 또는 데이터 집합 변경을 탐지할 때마다 Flow를 실행하는 시나리오 생성 가능.
- ex) 모델의 성능 드리프트를 자동으로 감지하여 모델 재교육 가능.
- ex) 로그 정리 또는 클러스터 시작 및 중지와 같은 일부 관리 작업을 자동화할 수 있음.

#### 1-2. Scenario Types

##### 1-2-1. step-based 

-  시나리오를 Dataiku의 visual Interface로 구성할 수 있음.

##### 1-2-2. custom Python script

- Python code로 정의 할 수 있음.

#### 1-3. Scenario components

##### 1-3-1. Trigger : 시나리오 실행 트리거

- Time-based trigger : 사용자가 정의한 정기적인 간격으로 시나리오 실행
- Dataset modification trigger : filesystem-based datasets에 사용하는 것으로 데이터 세트에서 변경 사항이 감지될 때마다 사용 (ex : 파일 용량 변화)
- SQL-based dataset trigger : 쿼리를 실행하고 쿼리의 출력이 마지막 실행과 관련하여 변경될 때 시나리오 실행 ex) : SELECT DISTINCT START_TIME FROM TRAFFIC; : START_TIME 이 변경될때 실행
- Python trigger : Python Script로 실행. 사용자가 설정.

##### 1-3-2. Sequence of Steps or Action : 사용자에 의해 구성. 여러 기능 있음.

- building or clearing a dataset
- training a model
- running metrics and checks
- refreshing the cache of charts and dashboards
- Writing custom code snippets in Python or SQL
- Managing clusters
- Defining variables at different levels
- Deployment-related actions, and more.

##### 1-3-3. Reporters : 시나리오(성공여부,경고,custom step)에 대해 검증 및 알림 기능

- Mail,
- Slack,
- Microsoft Teams,
- Webhook, and
- Twilio.

#### 1-4. Scenario Config

![scenario_config](.\image\scenario_config.PNG)



- grace delay : 트리거가 감지되고 시나리오가 시작될 때 까지의 시간 간격. ex) 데이터 세트에 새 행을 추가하는 등 변경 사항이 발생하는 동안 트리거 실행 방지.
- Re-check: 변경 사항이 발생하지 않도록 하기 위해 grace delay 후 트리거가 한 번 더 실행. 변경 사항이 발생한 경우 수정이 완료될 때까지 다시 한번 grace delay을 대기함.
- 

### 2. 23.05.11 Dataiku 세미나 선릉 위워크 2호점

#### 2-1) Dataiku Architecture Overview

- Unified Platform
  - 
- Node Types (중요)
  - DESIGN node : 설계 및 개발,
  - DEPLOYER node : 
  - AUTOMATION node :  모델 재배포 같은 것.
  - API service : 실시간 기능 처리 노드
- AUTOMATION node에서 나온 API와 API Production 을 배포하기전에 API Vaildation 기능 있음.
- Deployment (데이터 이쿠 설치 형태) : 데이터 이쿠를 어떻게 설치할지
  - 클라우드 환경에서 설치하는게 기능이 많고 좋음.
  - 온프레미스도 가능
- Containers : 클라우드 환경에서
  - 목적 : API node를 배포할때 사용
  - Node 버전 업 다운, 성능에 따라 재배포, 관리 쉬움.
  - 머신러닝, 파이썬을 컨테이너 레시피로 사용 가능.
  - DSS setting에서 관리
  - 파이썬 레시피에서 환경 셋팅 가능 (컨테이너, 파이썬 환경)
  - 컨테이너 별 리소스 설정 가능( CPU 같은 것.)
- Execution Engine
  - S3 ,하둡, db 에서 데이터 연결 다 가능
  - 데이터이쿠 자체에서의 컴퓨터 엔진을 사용할 수 있고 db에서의 컴퓨터 엔진을 사용할 수 도 있음.
  - DB에서 데이터를 가져올 때 레시피를 쓰고 다시 DB에 넣는 것 보다 DB 자체에서 전처리 후 저장된 데이터를 가져오는 것이 효율적.(prepare 레시피에서 Run 옆에 설정 아이콘에서 실행 엔진 선택 가능(근데 SQL로 변경이 불가능한 전처리가 포함되면 불가능)
  - Join 레시피 같은 것은 당연히 DB 엔진으로 변경 가능(속도 빠름.)
  - user 생성 및 프로젝트 복제 등 파이썬 레시피 코딩으로 생성 ,관리 가능

- EC2 같은곳에 Fleet 매니저 같은 것들 설치하면 쿠버네티스나 DSS 인스턴스 생성 및 관리 가능

- https://gallery.dataiku.com/home/ 실제 프로젝트 샘플들 볼 수 있음. 수정 및 실행 불가능

#### 2-2) 데모 자료 원기 전임님께 전달

- 데이터 파이프라인 생성에서부터 머신 러닝 모델의 생성, 사용 및 관리가 얼마나 간편해지는가?
- 협업 기반의 개발주기 단축이....
- 





### 3. 질문 Q&A

- 
- 

#### 4. Keyword 

- VPC : 하나의 큰 네트워크라고 이해. 
- Govern
- Fleet Manager : DSS instance 생성 하고 관리, 클라우드 환경의 Dataiku 기능
- Node Type에 따라 DSS 를 생성하는 방식으로 함. 
