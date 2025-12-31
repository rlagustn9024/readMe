# 엘림 워크스페이스 API 서버

## 1. 프로젝트 개요

개발 기간: 2025-07 ~ 2025~12

엘림 주식회사 기계설비·건축 프로젝트의 현장 점검 및 운영 데이터를 체계적으로 관리하고,
**점검 결과를 기반으로 보고서를 자동 생성**하기 위한 백엔드 API 서버입니다.


🔗 **서비스 URL**<br>
[엘림 주식회사 워크스페이스](https://elim.hs9024.cloud)입니다.

---

### 📄 보고서 자동화 Demo
#### 📌 **참고 | 보고서 자동화 워커 서비스**

> 보고서 자동 생성 로직은 API 서버와 분리된 **독립적인 애플리케이션**으로 구현되어 있습니다. (Python)

- 해당 구조를 통해 보고서 생성 작업이 서비스 전체 성능에 영향을 주지 않도록 설계
- 메시지 큐(SQS)를 통해 메세지를 전달받아 로컬에서 보고서 생성 작업 수행

👉 보고서 자동화 프로그램의 상세 구현 내용은  
아래 GitHub 저장소에서 확인할 수 있습니다. (권한 필요)

[🔗보고서 자동화 프로그램 깃허브](https://github.com/rlagustn9024/python-worker/tree/develop)

---

아래는 기계설비 점검 결과(서버 데이터)를 기반으로 
보고서를 자동 생성하는 프로세스 예시입니다. 

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/report-gui1.png" width="1000"/>
      <br/>
      <b>전체 템플릿 생성</b>
    </td>
    <td align="center">
      <img src="assets/images/example/machine/report/report-gui2.png" width="1000"/>
      <br/>
      <b>설비별 성능점검표 생성</b>
    </td>
  </tr>
</table>

<details>
  <summary><b>👉 생성 단계별 화면 더보기</b></summary>

<table align="center">
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/general/general-report.gif" width="800"/>
      <br/>
      <b>일반 보고서 생성 화면</b>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/inspection/inspection-report.gif" width="800"/>
      <br/>
      <b>설비별 성능점검표 생성</b>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/generate.gif" width="800"/>
      <br/>
      <b>실제 랜더링 화면</b>
    </td>
  </tr>
</table>

> ⚠️ **참고**
>
> 위 GIF에 표시되는 화면 중 `실제 랜더링 화면`은
> **보고서 생성 과정을 시각적으로 확인하기 위한 옵션 UI**이며,  
> **테스트용 데이터 및 테스트 이미지**를 기반으로 구성되어 있습니다.
>
> 실제 사용 환경에서는 해당 화면이 노출되지 않으며,  
> **백엔드에서 보고서 생성이 백그라운드 작업으로 자동 수행**됩니다.  
> (UI 출력 여부는 설정을 통해 활성화/비활성화 가능)

</details>

---

### 생성 완료된 보고서 예시
<details>
<summary><b>👉 보고서 예시 사진 보기</b></summary>

#### 일반 보고서

> 아래 이미지는 자동 생성된 보고서(HWP, 100+ 페이지) 중 **구조와 내용 이해를 위한 일부 페이지 발췌본**입니다.
>
> 보안 및 설명 목적에 따라 일부 이미지와 내용은 **의도적으로 편집·제거**되어 있으며,  
> 포함된 대부분의 사진 및 데이터는 **테스트용 샘플 데이터**를 기반으로 구성되어 있습니다.


<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/general/cover.png" width="400"/>
      <br/>
      <b>표지</b>
    </td>
    <td align="center">
      <img src="assets/images/example/machine/report/general/participant.png" width="400"/>
      <br/>
      <b>참여기술진 및 관리주체현황</b>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/general/quantity.png" width="400"/>
      <br/>
      <b>점검대상 설비 및 수량</b>
    </td>
    <td align="center">
      <img src="assets/images/example/machine/report/general/performance-inspection-result.png" width="400"/>
      <br/>
      <b>점검결과 내역서</b>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/general/performance-review.png" width="400"/>
      <br/>
      <b>성능점검시 검토사항</b>
    </td>
    <td align="center">
      <img src="assets/images/example/machine/report/general/general-report.png" width="400"/>
      <br/>
      <b>일반 보고서 파일</b>
    </td>
  </tr>
</table>
<br>

#### 설비별 성능점검표

> 아래 이미지는 자동 생성된 보고서(HWP, 100+ 페이지) 중 **구조와 내용 이해를 위한 일부 페이지 발췌본**입니다.
>
> 보안 및 설명 목적에 따라 일부 이미지와 내용은 **의도적으로 편집·제거**되어 있으며,  
> 포함된 대부분의 사진 및 데이터는 **테스트용 샘플 데이터**를 기반으로 구성되어 있습니다.


<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/inspection/inspection1.png" width="400"/>
      <br/>
      <b>설비별 성능점검표 예시1</b>
    </td>
    <td align="center">
      <img src="assets/images/example/machine/report/inspection/inspection2.png" width="400"/>
      <br/>
      <b>설비별 성능점검표 예시2</b>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/inspection/inspection1.png" width="400"/>
      <br/>
      <b>설비별 성능점검표 예시3</b>
    </td>
    <td align="center">
      <img src="assets/images/example/machine/report/inspection/inspection2.png" width="400"/>
      <br/>
      <b>설비별 성능점검표 예시4</b>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/report/general/general-report.png" width="400"/>
      <br/>
      <b>설비별 성능점검표 파일</b>
    </td>
  </tr>
</table>
</details>

---

## 2. 기술스택
[![My Skills](https://skillicons.dev/icons?i=java,js,spring,mysql,aws,prometheus,grafana,nginx,docker,postman)](https://skillicons.dev)

이외에도
- Spring JPA
- Spring Security
- QueryDSL

등을 사용했습니다.

---

## 3. 인프라 아키텍처
### 3-1) 사용자 요청 흐름 (프론트엔드)
사용자는 React 기반 프론트엔드 애플리케이션을 통해 서비스를 이용합니다.<br> 
프론트엔드 리소스 요청은 다음 흐름으로 처리됩니다.

![frontend.png](assets/images/infra/frontend.png)

1. 사용자가 브라우저를 통해 서비스 도메인에 접속
2. DNS 요청은 Route 53을 통해 처리 (CloudFront에서 CNAME 응답 받으면, Vercel에 또 요청해서 IP주소 받음)
3. 정적 리소스 요청은 Vercel에 배포된 React 애플리케이션으로 전달 (SPA)
4. HTTPS 기반으로 프론트엔드 리소스를 사용자에게 제공

---

### 3-2) API 요청 흐름 (백엔드)

프론트엔드에서 발생하는 API 요청은 다음과 같은 흐름으로 처리됩니다.

![backend.png](assets/images/infra/backend.png)

1. 프론트엔드에서 API 요청 발생
2. Route 53을 통해 API 도메인으로 요청 전달
3. CloudFront를 통해 요청을 수신하여 EC2에 전달 (현재는 단일 인스턴스)
4. 사진 및 파일 데이터는 AWS S3에 저장 (presigned url 사용)

---

### 3-3) 서버 구성 (EC2 내부)
EC2 인스턴스 내부는 Docker 기반 컨테이너 환경으로 구성되어 있습니다.

![ec2.png](assets/images/infra/ec2.png)

- **Nginx**
  - 외부 요청을 수신하는 리버스 프록시 역할
  - 접근 로그 및 요청 흐름 제어


- **Spring Boot API 서버**
  - 핵심 비즈니스 로직 처리


- **Prometheus**
  - JVM 및 애플리케이션 메트릭 수집 (EC2 포함)
  - AlertManager와 연동됨


- **Grafana**
  - 수집된 메트릭 시각화 및 대시보드 제공

---

### 3-4) AWS 인프라 구성
| 서비스 | 사용 목적 |
|------|----------|
| **EC2** | Spring Boot API 서버 운영 |
| **RDS (MySQL)** | 애플리케이션 데이터 저장 |
| **S3** | 점검 사진 및 보고서 파일 저장 |
| **CloudFront** | API 및 정적 리소스 CDN |
| **Route 53** | 서비스 도메인 DNS 관리 |
| **SQS** | 보고서 생성 작업 메시지 전달 |
| **EventBridge** | ECR 이미지 Push 이벤트 감지 |
| **Lambda** | EC2 배포 트리거 자동화 |
| **ECR** | Docker 이미지 저장소 |

----

### 3-5) 운영 / 모니터링 구성
| 구성 요소 | 역할 |
|---------|------|
| **Docker** | 컨테이너 기반 실행 환경 |
| **Nginx** | Reverse Proxy 및 요청 라우팅 |
| **Prometheus** | JVM 및 시스템 메트릭 수집 |
| **Grafana** | 메트릭 시각화 및 대시보드 |
| **Alertmanager** | 장애 및 임계치 초과 알림 |


----

## 4. 주요 기능
### 🔹 프로젝트 / 현장 관리
> 기계설비 프로젝트(현장)를 기준으로 점검 대상, 일정, 참여 기술진을 통합 관리합니다.

<table align="center">
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/project/project-read1.png" width="1000"/>
      <br/>
      <b>프로젝트(현장) 관리</b>
    </td>
  </tr>
</table>

<details>
<summary><b>👉 프로젝트 / 현장 관리 화면 더보기</b></summary>

<table align="center">
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/project/project-create1.png" width="1000"/>
      <br/>
      <b>프로젝트(현장) 생성</b>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/project/project2.png" width="1000"/>
      <br/>
      <b>현장 정보</b>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/project/project-schedule.png" width="1000"/>
      <br/>
      <b>점검일정 및 참여기술진</b>
    </td>
  </tr>
</table>
</details>

- 기계설비 프로젝트(현장) 생성 및 관리
- 현장 별 점검 일정과 참여 기술진 관리

---

### 🔹 점검 설비 및 결과 관리
> 현장에 등록된 설비별로 점검 항목, 점검 세부 항목, 점검 결과, 미흡사항 및 조치 필요사항 등을 관리
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/inspection/inspections.png" width="1000"/>
      <br/>
      <b>설비 목록</b>
    </td>
  </tr>
</table>

<details>
<summary><b>👉 점검 설비 및 결과 관리 화면 더보기</b></summary>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/inspection/inspection-basic.png" width="1000"/>
      <br/>
      <b>설비별 성능점검표 기본 정보</b>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/inspection/inspection-checklist1.png" width="1000"/>
      <br/>
      <b>설비1 점검내용</b>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/inspection/inspection-checklist2.png" width="1000"/>
      <br/>
      <b>설비2 점검내용</b>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/inspection/deficiencies.png" width="1000"/>
      <br/>
      <b>미흡사항 및 조치필요사항</b>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/inspection/inspection-checklist-subitem1.png" width="1000"/>
      <br/>
      <b>점검 세부 항목</b>
    </td>
  </tr>
</table>
</details>

---

### 🔹 전체 사진
> 현장 점검 과정에서 촬영된 사진 데이터를 관리
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/pic/all-pics.png" width="1000"/>
      <br/>
      <b>전체 사진</b>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/machine/pic/inspection-pic.png" width="1000"/>
      <br/>
      <b>사진 상세정보</b>
    </td>
  </tr>
</table>

- 무한 스크롤 방식으로 30개 단위 조회
- 현장 1곳당 최소 300장 ~ 최대 1,000장 이상의 사진 관리

---

### 🔹 직원 관리
> 회사에 재직중인 직원의 정보를 탭 단위로 관리
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/member/member-page.png" width="1000"/>
      <br/>
      <b>직원 관리 페이지</b>
    </td>
  </tr>
</table>

<details>
<summary><b>👉 직원 관리 화면 더보기</b></summary>

<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/member/privacy.png" width="1000"/>
      <br/>
      <b>개인정보 탭</b>
    </td>
  </tr>
</table>
</details>

- 기본정보, 개인정보, 재직정보, 경력정보, 기타정보 탭으로 구성됨 

---

### 🔹 권한 관리
> 직원별 역할에 따른 접근 권한을 제어
- 백엔드 API 개발 완료. 프론트엔드 개발 필요

---

### 🔹 라이선스 관리
> 회사 라이선스 정보를 관리
<table>
  <tr>
    <td align="center">
      <img src="assets/images/example/license/license-page.png" width="1000"/>
      <br/>
      <b>라이선스 관리 페이지</b>
    </td>
    <td align="center">
      <img src="assets/images/example/license/license-info.png" width="1000"/>
      <br/>
      <b>라이선스 정보</b>
    </td>
  </tr>
</table>


---

## 5. API 문서

#### **Swagger API 문서**
[🔗 Swagger API 문서](https://d2qmtzuf9ioakk.cloudfront.net/swagger/index.html)
- OpenAPI(Swagger) 기반 API 문서입니다.
- API 서버와 분리하여 S3 + CloudFront로 정적 배포


#### **API 테스트**
- Postman을 사용하여 요청/응답 테스트를 진행했습니다.


---

## 6. 실행 및 배포
### 6-1. CI / CD 파이프라인

Github Actions와 AWS를 활용하여 코드 수정부터 EC2 배포까지의
전 과정을 자동화는 CI / CD 파이프라인입니다.

![img.png](assets/images/infra/pipeline.png)

- Gitgub Actions와 AWS(ECR, EventBridge, Lambda, EC2)를 활용한 배포 자동화 구성 
- 개발자가 지정한 브랜치에 코드를 push하면, Docker 이미지 빌드부터 EC2 배포까지 자동 수행


> 지정한 브랜치에 push 시 아래와 같은 흐름으로 배포 자동화가 이루어집니다.
(평소에는 .disabled로 무효화한 채로 관리)

#### 동작 흐름
1. 개발자가 deploy.yml에 설정된 브랜치에 코드를 Push
2. GitHub Actions 실행
    - GitHub Actions 워크플로우가 트리거됨
    - Dockerfile을 기반으로 애플리케이션 Docker Image 빌드
3. AWS ECR 업로드
    - 생성된 도커 이미지를 AWS ECR에 업로드
    - 이미지 업로드 완료 이벤트 발생
4. EventBridge에서 이벤트 감지 후 사전에 설정된 규칙에 따라 AWS Lambda 트리거
5. Lambda 함수가 EC2에 배포 명령 전달. EC2에서 ECR에서 최신 Docker Image Pull 수행 (권한 이미 부여되어 있음)
6. EC2 배포 수행
    - 기존 컨테이너 종료 후 신규 도커 이미지 기반 컨테이너 실행

---

## 7. 기타
### 7-1) 디렉토리 구조
```
src/main/java/com/elimsafety/server
├─ domain                # 비즈니스 도메인 영역
│  ├─ auth               # 인증/인가
│  ├─ contract           # 계약
│  ├─ engineer           # 기술진
│  ├─ license            # 라이선스
│  ├─ member             # 회원
│  │  ├── api            # 컨트롤러
│  │  ├── application    # 서비스
│  │  ├── dao            # 리포지토리
│  │  ├── domain         # Entity, Enum
│  │  └── dto            # 요청/응답 DTO
│  ├─ machine            # 기계설비
│  ├─ report             # 보고서
│  └─ safety             # 안전진단
│
├─ global                # 공통 영역
│  ├─ cache              # 캐시 (Caffeine)
│  ├─ common             # 공통 엔티티 / 상수 / DTO
│  ├─ config             # 설정 (Swagger, Querydsl 등)
│  ├─ security           # 인증/인가 필터, JWT (SecurityConfig 포함)
│  ├─ docs               # Swagger Docs
│  ├─ exception          # 글로벌 예외 처리
│  ├─ infra              # 외부 연동 (AWS SQS, S3 등)
│  ├─ event              # 이벤트 (보고서 관련 처리)
│  └─ util               # 공통 유틸리티
│
└─ ServerApplication
```


### 7-2) 테이블 정의서
**Notion 기반 테이블 정의서**
- [테이블 정의서(Core)](https://handsome-pyramid-9ff.notion.site/28bdaf54079580158793c7cb07fc7dfe)
- [테이블 정의서(기계설비)](https://handsome-pyramid-9ff.notion.site/2c4daf54079580f99a7ada60ecb74986)
- [테이블 정의서(건축)](https://handsome-pyramid-9ff.notion.site/2c4daf540795807a85d0fa76890cc6bb)

---

### 7-3) ERD
> ERD 이미지는 draw.io를 통해 작성·관리되며, 본 문서에는 주요 구조를 시각화하여 첨부합니다.

#### **Core ERD**
> 회원, 인증, 권한 등 비즈니스 도메인과 분리된 시스템 핵심 영역

![ERD(공통)](./assets/images/architecture/ERD(Core).png)

#### **기계설비 ERD**
> 기계설비 관련 도메인

![ERD(기계설비)](./assets/images/architecture/ERD(기계설비).png)

#### **건축(안전진단) ERD**
> 건축(안전진단) 관련 도메인

![ERD(건축)](./assets/images/architecture/ERD(건축).png)


---
