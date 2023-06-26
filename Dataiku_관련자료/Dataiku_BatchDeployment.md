# Dataiku Project Deployment

- 참고 :https://academy.dataiku.com/path/mlops/projects-in-production/1069661

### 1. Dataiku Project 배포

- Project Deployer가 Design node의 project를 Automation node에 있는 bundle로 전환하여 project를 변환함.
  - Project에는 metrics, checks, reporter, optimized pipeline, well-documented workflow 등을 포함한 secenario가 있음.
- Project Deployer 가 수행할 수 있는 작업
  - 모든 Automation Node 관리
  - Automation Node에 Bundle 배포
  - 배포된 Automation Node의 프로젝트 상태 모니터링

![batch_deployment](./image/batch_deployment.png)

#### 1-1. 배포 주의사항

- Design Node에서 plugin이나 개발 환경이 있으면 Automation Node에도 같이 배포 해야 함.
- Design Node를 Bundle로 만들고 Automation Node에 배포 하기전에 Infrastructure가 구성되어야 함.

#### 1-2. Project Deployer Architecture

- Local or Standalone Deployer 설치 및 설정 :https://doc.dataiku.com/dss/latest/deployment/setup.html#using-a-standalone-deployer
- Local Deployer : 사용자의 Infratructure에서 하나의 Design or Automation node가 있는 경우, Project Deployer는 Dataiku Node 자체의 일부로 될 수 있음. 따로 추가 설정이 불필요함.
- Standalone/Remote Deployer : 사용자의 Infrastructure에서 여러 Design and/or Automation node가 있는 경우, 모든 Design and/or Automation node에 대해 중앙 집중식 배포자 역할을 하는 별도의 DSS노드를 설치할 수 있음.

![Infrastructure](./image/Infrastructure.PNG)

#### 1-3. Project Deployer

- 참고 : https://doc.dataiku.com/dss/12/deployment/index.html
- DSS의 Production deployments는 deployer라는 중앙 위치에서 관리. 배포자는 일반적으로 DSS 클러스터의 전용 노드로 배포되지만 Design or Automation Node에서 Local로 실행될 수도 있음.
- DSS Automation Node는 DSS 개발 및 운영 환경을 분리할 수 있는 방법을 제공하며 운영 중인 DSS 프로젝트를 쉽게 배포하고 업데이터할 수 있도록 함.
- DSS Design Node는 개발 환경이고 Flow를 설계하고 데이터 로직을 구축하거나 개선할 수 있는 곳임. Design Node가 테스트되고 새 버전이 릴리스 및 배포될 준비가 되면 Automation Node에 배포함.

##### 1-3-1. Automation Node 장점

- Automation Node의 Metric과 시나리오를 사용하면 Model의 성능을 보다 효과적으로 평가하고 실제 production 데이터를 보다 효과적으로 제어 가능.

#### 참고 

- Design Node에 내장된 프로젝트를 Automation Node에 배포하는 작업은 Project Bundle을 사용하여 프로젝트 레벨에서 수행됨.
