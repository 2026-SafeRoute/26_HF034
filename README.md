<!-- 📷 [이미지] 서비스 로고 : src에 로고 이미지 URL 넣기 (제목 왼쪽에 붙어요, 권장 가로 110px) -->
# Safe Route <img width="110" align="left" alt="SafeRoute 로고" src="https://github.com/user-attachments/assets/ae3ee84e-ef09-4d46-a864-c0243c664cb9" />

![SafeRoute](https://img.shields.io/badge/Safe%20Route-AI%C2%B7IoT%20%EA%B8%B0%EB%B0%98%20%EC%8B%A4%EC%8B%9C%EA%B0%84%20%ED%99%94%EC%9E%AC%20%EB%8C%80%ED%94%BC%20%ED%9B%88%EB%A0%A8%20%EA%B4%80%EB%A6%AC%20%ED%94%8C%EB%9E%AB%ED%8F%BC-DBEAFE?style=for-the-badge&labelColor=2563EB)

<br/>

<p>
  <img alt="React" src="https://img.shields.io/badge/React-18-149ECA?logo=react&logoColor=white" />
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-5.6-3178C6?logo=typescript&logoColor=white" />
  <img alt="Spring Boot" src="https://img.shields.io/badge/Spring%20Boot-3.5-6DB33F?logo=springboot&logoColor=white" />
  <img alt="Java" src="https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white" />
  <img alt="Python" src="https://img.shields.io/badge/Python-3.9+-3776AB?logo=python&logoColor=white" />
  <img alt="YOLOv8" src="https://img.shields.io/badge/YOLOv8-Hailo--8L-111F68?logo=yolo&logoColor=white" />
  <img alt="Raspberry Pi" src="https://img.shields.io/badge/Raspberry%20Pi-5-A22846?logo=raspberrypi&logoColor=white" />
  <img alt="AWS" src="https://img.shields.io/badge/AWS-EC2%20%7C%20S3%20%7C%20DynamoDB-FF9900?logo=amazonwebservices&logoColor=white" />
</p>

<p>
  <a href="#1-프로젝트-개요">프로젝트 개요</a>
  ·
  <a href="#2-팀원-소개">팀원 소개</a>
  ·
  <a href="#3-시스템-구성도">시스템 구성도</a>
  ·
  <a href="#4-작품-소개영상">작품 소개영상</a>
  ·
  <a href="#5-핵심-소스코드">핵심 소스코드</a>
</p>

<!--
| Repository | 설명 |
| :--- | :--- |
| [SafeRoute-FE](https://github.com/2026-SafeRoute/SafeRoute-FE) | 관리자 웹 대시보드 (React · TypeScript) |
| [SafeRoute-BE](https://github.com/2026-SafeRoute/SafeRoute-BE) | API · 경로 탐색 · 실시간 이벤트 서버 (Spring Boot) |
| [SafeRoute-AI](https://github.com/2026-SafeRoute/SafeRoute-AI) | 도면 세그멘테이션 서버 · 엣지 혼잡도 분석 · 유도등 제어 (Python) |

<br />
-->

<!-- 📷 [이미지] 서비스 대표 이미지 : src에 이미지 URL 넣기 (권장 16:9) -->
<!-- <p align="center">
  <img width="900" alt="SafeRoute 대표 이미지" src="" />
</p> -->

<br />

## 💡1. 프로젝트 개요

### 1-1. 프로젝트 소개
- 프로젝트 명 : Safe Route: AI·IoT 기반 실시간 화재 훈련 대피 관리 플랫폼
- 프로젝트 정의 : AI 비전 분석과 IoT 비상유도등을 연동해 훈련 중 혼잡·병목을 실시간으로 파악하고, 대피 경로를 재계산해 유도등 방향을 바꾸며, 훈련 결과를 자동으로 평가하는 화재 대피 훈련 관리·평가 플랫폼


### 1-2. 개발 배경 및 필요성
- 국내에서는 최근 10년간 매년 3만 8천여 건의 화재가 발생하고 있으며, 2025년에는 38,344건의 화재로 346명이 사망해 전년 대비 사망자가 12.3% 늘었습니다.<sup>[1]</sup>
- 화재 피해를 줄이는 핵심은 '대피'지만, 법정 소방훈련은 연 1회 이상 실시하도록 되어 있을 뿐<sup>[2]</sup> 실제 훈련은 정해진 경로와 시간을 확인하는 데 그치고 있습니다.
- 또한 인력 중심의 관찰과 사후 평가에 의존하기 때문에, 훈련 중 어느 구간에서 사람이 몰리고 병목이 생기는지 실시간으로 파악하기 어렵습니다.
- 학교·캠퍼스 이용자 39명을 대상으로 한 설문조사(2026.08.31 ~ 09.07) 결과, 혼잡에 대한 우려가 크고 기존 훈련에 대한 체감 효과는 낮았습니다.

  <img width="600" alt="설문조사 결과" src="https://github.com/user-attachments/assets/8ebb1c0b-43f4-4ead-9058-d45308053572" />

 → 따라서 혼잡을 실시간으로 감지해 대피 인원을 분산 유도하고, 훈련 결과를 정량적으로 평가해 다음 훈련을 개선할 수 있는 플랫폼이 필요합니다.

<sub>[1] 소방청, "화재발생 현황(2025년도)," e-나라지표, 2026.<br>[2] 법제처, "화재의 예방 및 안전관리에 관한 법률 시행규칙," 제36조, 국가법령정보센터, 2026.</sub>

### 1-3. 프로젝트 특장점
- 건물 도면 이미지를 U-Net 세그멘테이션으로 분석해 벽·복도·계단·문을 구분하고 노드-엣지 디지털 맵으로 자동 변환
- 화재 확산 시뮬레이션으로 훈련 전에 경로가 막히는 시점과 재탐색 경로를 미리 진단
- CCTV 영상을 Raspberry Pi 5 + Hailo-8L 엣지 디바이스에서 YOLOv8로 직접 분석해 구간별 인원과 밀도 기반 혼잡도를 실시간 산출
- 혼잡 구간은 가중치를 높이고 화재 구간은 완전히 제외하는 다익스트라 기반 대피 경로 재계산
- 경로 재산출 결과를 관리자가 승인하면 층 전체 IoT 유도등 방향이 출구 쪽 다음 노드 방향으로 자동 갱신
- 대피 시간·대피 성공률·병목 발생·경로 이탈률을 가중 합산한 A~F 등급 평가 보고서 자동 생성

### 1-4. 주요 기능

<table>
  <tr>
    <th width="90">단계</th>
    <th width="150">기능</th>
    <th>설명</th>
  </tr>
  <tr></tr>
  <tr>
    <td align="center" rowspan="5"><b>사전 준비</b></td>
    <td><b>디지털 맵 생성·편집</b></td>
    <td>• 도면 AI 세그멘테이션 후 노드·엣지 자동 생성<br>• CCTV·유도등·출입구 등 POI 수동 보정<br>• 도면 경로 진단 : 탈출구에 닿지 못하는 노드, 탈출구 미지정 계단, 시작 후보별 도달 가능한 탈출구 수 확인<br>• 훈련 준비 체크리스트</td>
  </tr>
  <tr></tr>
  <tr>
    <td><b>훈련 시나리오 설정</b></td>
    <td>• 도면 위 발화 위치·시작 노드 지정<br>• 확산 속도·참가 인원·훈련 일시 설정, 임시 저장<br>• 시나리오 경로 진단 : 화재 확산 시뮬레이션으로 처음 경로, 예상 재탐색 경로, 경로가 막히는 예상 시점 미리보기</td>
  </tr>
  <tr></tr>
  <tr>
    <td><b>건물·설비 관리</b></td>
    <td>• 건물 등록·수정·삭제, 층별 도면 관리<br>• CCTV·유도등 등록 및 상태 관리</td>
  </tr>
  <tr>
    <td align="center" rowspan="7"><b>훈련 진행</b></td>
    <td><b>실시간 훈련 제어</b></td>
    <td>• 대기 → 진행 → 종료 상태 관리 (최대 10분)<br>• 화재 확산 반영<br>• 병목 감지 시 경로 재계산 제안 및 승인·거절</td>
  </tr>
  <tr></tr>
  <tr>
    <td><b>AI 혼잡도 분석</b></td>
    <td>• 구역별 인원 집계<br>• 감시 면적 대비 밀도로 정상·주의·혼잡·매우 혼잡 4단계 판정<br>• 혼잡 이벤트 및 캡처 이미지 전송</td>
  </tr>
  <tr></tr>
  <tr>
    <td><b>IoT 유도등 제어</b></td>
    <td>• 서버 명령 큐를 Pi가 폴링<br>• 이더넷 릴레이로 유도등 방향(LEFT / RIGHT / BOTH / OFF) 제어 후 ACK 보고</td>
  </tr>
  <tr></tr>
  <tr>
    <td><b>훈련 모니터링</b></td>
    <td>• CCTV별 최신 프레임, 감지 인원·밀집도<br>• 이벤트 타임라인 실시간 확인</td>
  </tr>
  <tr>
    <td align="center"><b>훈련 후</b></td>
    <td><b>훈련 평가·보고서</b></td>
    <td>• 종합 등급·항목별 점수<br>• 대피 인원 누적 추이·최근 5회 대피 시간 차트<br>• 강점·개선점·권고사항, PDF 다운로드</td>
  </tr>
</table>


#### 💻 구현 화면

<table>
  <tr>
    <td align="center" width="50%"><img width="100%" alt="도면 관리 상세" src="https://github.com/user-attachments/assets/67b28ceb-ac77-44e4-bc8b-4dcb93ea6bbb" /></td>
    <td align="center" width="50%"><img width="100%" alt="시나리오 설정" src="https://github.com/user-attachments/assets/b9fe8992-ca39-4f47-99b6-49e9ab29d05f" /></td>
  </tr>
  <tr>
    <td align="center"><b>도면 관리 상세</b><br>노드 · 엣지 편집 · 경로 진단 · 훈련 준비 체크리스트</td>
    <td align="center"><b>시나리오 설정</b><br>발화 위치 · 시작 지점 지정 · 처음 경로와 재탐색 경로 미리보기</td>
  </tr>
  <tr>
    <td align="center" width="50%"><img width="100%" alt="훈련 진행" src="https://github.com/user-attachments/assets/11a211dc-b35b-4463-b202-574a6e7a5ab9" /></td>
    <td align="center" width="50%"><img width="100%" alt="훈련 모니터링 상세" src="https://github.com/user-attachments/assets/4cb52144-c325-452e-9c2f-7bc0c984b270" /></td>
  </tr>
  <tr>
    <td align="center"><b>훈련 진행</b><br>화재 확산 · 실시간 경로 · 재탐색 경로 승인/거절</td>
    <td align="center"><b>훈련 모니터링 상세</b><br>CCTV 프레임 · 감지 인원 · 혼잡 단계 · 이벤트 타임라인</td>
  </tr>
  <tr>
    <td align="center" width="50%"><img width="100%" alt="분석 보고서" src="https://github.com/user-attachments/assets/4fd6bb05-9a57-46e7-aa7c-acfde3733dc8" /></td>
    <td align="center" width="50%"><img width="100%" alt="홈 대시보드" src="https://github.com/user-attachments/assets/ce08376b-bf59-43c5-814e-af9bf5bdc3bb" /></td>
  </tr>
  <tr>
    <td align="center"><b>분석 보고서</b><br>종합 등급 · 항목별 점수 · 통계 차트 · 권고사항</td>
    <td align="center"><b>홈 대시보드</b><br>핵심 지표 · 최근 훈련 기록 · 예정된 훈련</td>
  </tr>
</table>


<br />

### 1-5. 기대 효과 및 활용 분야
- 기대 효과
  - **데이터 기반 정량 평가 체계 구축** : IP 카메라 기반 혼잡도 분석으로 대피 과정 데이터를 수집하고, 전체 대피 소요 시간·구역별 최대 인원·혼잡 발생 위치와 지속 시간·출구별 이용 인원을 평가 지표로 산출해 후속 훈련 시나리오와 대피 동선 개선에 활용
  - **AI 영상 분석과 IoT 비상유도등 연계를 통한 현장 대응 체계 구축** : 영상 분석, 경로 재계산, 유도등 방향 변경까지 이어지는 현장 대응 체계로 혼잡하지 않은 경로로 인원을 분산해 혼잡 발생 시간과 대피 지연 감소
  - **기존 서비스와의 차별성 확보** : 훈련 준비부터 평가 보고서까지 전 과정을 단일 플랫폼에서 지원하고, 다양한 훈련 시나리오로 상황별 대피 유도 가능
- 활용 분야
  - **초·중·고등학교 정기 화재 대피 훈련 평가 시스템** : 정기 화재 대피 훈련을 실시하는 학교와 안전 담당자가 대피 소요 시간, 혼잡 발생 위치, 대피 지연 구간, 대피 성공률을 파악하고 보고서를 바탕으로 대피 경로·안전요원 배치 위치·훈련 시나리오를 보완
  - **기숙사·대학교 캠퍼스 안전 관리 시스템** : 여러 계단과 출구가 연결된 다중이용 건물에서 특정 구간에 인원이 집중될 수 있는 다양한 상황을 반영한 시나리오로 훈련
 

### 1-6. 기술 스택

<table>
  <tr>
    <th width="160">분야</th>
    <th>기술</th>
  </tr>
  <tr>
    <td align="center" width="160"><b>프론트엔드</b></td>
    <td><img alt="React" src="https://img.shields.io/badge/React-149ECA?style=for-the-badge&logo=react&logoColor=white" /> <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" /> <img alt="Vite" src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" /> <img alt="vanilla-extract" src="https://img.shields.io/badge/vanilla--extract-DB7093?style=for-the-badge" /> <img alt="TanStack Query" src="https://img.shields.io/badge/TanStack%20Query-FF4154?style=for-the-badge&logo=reactquery&logoColor=white" /> <img alt="Zustand" src="https://img.shields.io/badge/Zustand-443E38?style=for-the-badge" /></td>
  </tr>
  <tr>
    <td align="center" width="160"><b>백엔드</b></td>
    <td><img alt="Java 17" src="https://img.shields.io/badge/Java%2017-007396?style=for-the-badge&logo=openjdk&logoColor=white" /> <img alt="Spring Boot" src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" /> <img alt="Spring Data JPA" src="https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white" /> <img alt="WebSocket (STOMP)" src="https://img.shields.io/badge/WebSocket%20%28STOMP%29-010101?style=for-the-badge" /></td>
  </tr>
  <tr>
    <td align="center" width="160"><b>AI / ML</b></td>
    <td><img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" /> <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" /> <img alt="U-Net" src="https://img.shields.io/badge/U--Net-555555?style=for-the-badge" /> <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" /> <img alt="YOLOv8" src="https://img.shields.io/badge/YOLOv8-111F68?style=for-the-badge&logo=yolo&logoColor=white" /> <img alt="OpenCV" src="https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" /> <img alt="ONNX Runtime" src="https://img.shields.io/badge/ONNX%20Runtime-005CED?style=for-the-badge&logo=onnx&logoColor=white" /> <img alt="NetworkX" src="https://img.shields.io/badge/NetworkX-2C5BB4?style=for-the-badge" /> <img alt="scikit-image" src="https://img.shields.io/badge/scikit--image-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white" /></td>
  </tr>
  <tr>
    <td align="center" width="160"><b>데이터베이스</b></td>
    <td><img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" /> <img alt="Amazon DynamoDB" src="https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=for-the-badge&logo=amazondynamodb&logoColor=white" /> <img alt="Amazon S3" src="https://img.shields.io/badge/Amazon%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white" /></td>
  </tr>
  <tr>
    <td align="center" width="160"><b>HW / IoT</b></td>
    <td><img alt="Raspberry Pi 5" src="https://img.shields.io/badge/Raspberry%20Pi%205-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white" /> <img alt="Hailo-8L NPU" src="https://img.shields.io/badge/Hailo--8L%20NPU-00A3E0?style=for-the-badge" /> <img alt="IP Camera (RTSP)" src="https://img.shields.io/badge/IP%20Camera%20%28RTSP%29-333333?style=for-the-badge" /> <img alt="Ethernet Relay (Modbus)" src="https://img.shields.io/badge/Ethernet%20Relay%20%28Modbus%29-555555?style=for-the-badge" /> <img alt="IoT 유도등" src="https://img.shields.io/badge/IoT%20%EC%9C%A0%EB%8F%84%EB%93%B1-2EA44F?style=for-the-badge" /></td>
  </tr>
  <tr>
    <td align="center" width="160"><b>클라우드 / 배포</b></td>
    <td><img alt="Amazon EC2" src="https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white" /> <img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" /> <img alt="Nginx" src="https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white" /> <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" /> <img alt="GHCR" src="https://img.shields.io/badge/GHCR-181717?style=for-the-badge&logo=github&logoColor=white" /> <img alt="Vercel" src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" /></td>
  </tr>
  <tr>
    <td align="center" width="160"><b>협업</b></td>
    <td><img alt="GitHub" src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" /> <img alt="Notion" src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white" /> <img alt="Discord" src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" /> <img alt="Figma" src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white" /></td>
  </tr>
</table>

<br />

## 💡2. 팀원 소개

<table align="center">
  <tr>
    <td align="center"><!-- <a href="https://github.com/urapp13ofmyeye"> --><img width="80" height="100" alt="멘티1" src="https://github.com/urapp13ofmyeye.png"><!-- </a> --></td>
    <td align="center"><!-- <a href="https://github.com/soyyyyy"> --><img width="80" height="100" alt="멘티2" src="https://github.com/soyyyyy.png"><!-- </a> --></td>
    <td align="center"><!-- <a href="https://github.com/songmin0111"> --><img width="80" height="100" alt="멘티3" src="https://github.com/songmin0111.png"><!-- </a> --></td>
    <td align="center"><!-- <a href="https://github.com/kyeonG0210"> --><img width="80" height="100" alt="멘티4" src="https://github.com/kyeonG0210.png"><!-- </a> --></td>
    <td align="center"><!-- <a href="https://github.com/hakSick"> --><img width="80" height="100" alt="멘티5" src="https://github.com/hakSick.png"><!-- </a> --></td>
    <td align="center"><img width="80" height="100" alt="멘토" src="https://github.com/user-attachments/assets/ae3ee84e-ef09-4d46-a864-c0243c664cb9"></td>

  </tr>
  <tr>
    <td align="center"><b>멘티1</b></td>
    <td align="center"><b>멘티2</b></td>
    <td align="center"><b>멘티3</b></td>
    <td align="center"><b>멘티4</b></td>
    <td align="center"><b>멘티5</b></td>
    <td align="center"><b>멘토</b></td>
  </tr>
  <tr>
    <td align="center">PM<br>FE • Design<br>HW</td>
    <td align="center">FE • Design<br>HW</td>
    <td align="center">BE • AI<br>HW • Infra</td>
    <td align="center">BE • HW<br>Infra</td>
    <td align="center">BE • AI<br>HW • Infra</td>
    <td align="center">프로젝트&nbsp;멘토<br>기술&nbsp;자문</td>
  </tr>
</table>

<br />


## 💡3. 시스템 구성도

### 3-1. 시스템 아키텍처

<p align="center">
  <img width="800" alt="시스템 아키텍처" src="https://github.com/user-attachments/assets/0c672212-05ef-4244-8d3d-5effb29d2b66" />
</p>

### 3-2. 서비스 구성도

<p align="center">
  <img width="800" alt="서비스 구성도" src="https://github.com/user-attachments/assets/550e90aa-96a6-4d14-ae8b-cc227a5787c4" />
</p>

| 단계 | 동작 과정 |
| :---: | :--- |
| 사전&nbsp;구축 | 도면 업로드 → AI 세그멘테이션(벽·복도·계단·문 구분) → 노드·엣지 자동 변환 → PostgreSQL 저장 → 관리자 POI 보정·경로 검증 |
| 훈련&nbsp;시작 | 발화 위치·시작 노드 지정 → 화재 회피 다익스트라 최단 경로 탐색 → 도면 위 기본 경로와 유도등 초기 방향 표시 |
| 혼잡&nbsp;감지 | IP 카메라 RTSP 수신 → Raspberry Pi 5 + Hailo-8L YOLOv8 사람 탐지 → 밀도 기반 혼잡도 판정 → 관측값·이벤트 서버 전송, 캡처 이미지 S3 업로드 |
| 경&#8288;로&nbsp;재&#8288;계&#8288;산 | 혼잡 구간 가중치 상향·화재 구간 제외 → 우회 경로 산출 → 관리자 승인 → 유도등 명령 적재 → Pi 폴링·릴레이 제어 → ACK 보고 |
| 결과&nbsp;확인 | 참가자는 유도등 방향을 따라 분산 대피, 관리자는 대시보드와 자동 생성된 평가 보고서로 결과 확인 |


### 3-3. 서비스 흐름도

<p align="center">
  <img width="800" alt="서비스 흐름도 간단한 버전" src="https://github.com/user-attachments/assets/cb06914c-d590-4fd4-80ef-1551f9f5b581" />
</p>

### 3-4. 하드웨어 구성도

<p align="center">
  <img width="800" alt="하드웨어 구성도" src="https://github.com/user-attachments/assets/c82eeaec-b0ee-473e-9ddc-a755138700a2" />
</p>


### 3-5. 엔티티 관계도 (ERD)
<p align="center">
  <img width="800" alt="ERD" src="https://github.com/user-attachments/assets/a4811a33-f03e-4506-b936-4b8477b5196a" />
</p>

### 3-6. 핵심 알고리즘

#### ① 도면 자동 인식 · 노드/엣지 변환

```
[도면 업로드] 관리자 → BE 서버 : 도면 이미지 · 실측 가로/세로(m) · 그리드 셀 크기 전달
      │
      ▼
BE 서버 → S3 : 도면 이미지 저장  →  AI 서버(FastAPI) : 분석 요청
      │
      ▼
U-Net 세그멘테이션 → 벽 · 방 · 복도 · 문 · 창문 · 계단 6개 클래스로 픽셀 분류
      │
      ▼
이동 가능 영역 추출 → 출구 · 계단 · 교차점은 노드, 통로는 엣지로 변환
      → 실측 크기를 반영해 엣지 거리(m) 계산
      │
      ▼
BE 서버 : 노드 · 엣지 · 그리드 셀을 PostgreSQL에 저장
      │
      ▼
관리자 보정 : 노드 · 엣지 수동 편집, 최종 탈출구(EXIT) 지정, CCTV · 유도등 위치 배치
      │
      ▼
훈련 준비 검증 : 시작 노드 · 최종 탈출구 지정 + 다익스트라 경로 탐색 성공 시 훈련 가능
```

#### ② 엣지 AI 혼잡도 분석

```
[훈련 시작] Raspberry Pi → BE 서버 : 훈련 활성 여부 · 임계값 · 감시 면적 설정 조회
      │
      ▼  (5 FPS)
IP 카메라 RTSP 영상 수신 → Hailo-8L NPU에서 YOLOv8 사람 탐지
      │
      ▼
ROI(감시 구역) 안의 인원 집계 → 밀도 = 인원 ÷ 감시 면적(㎡)
      │
      ▼
밀도를 임계값과 비교 → NORMAL / CAUTION / CROWDED / VERY_CROWDED 분류
      │
      ├─ 집계 구간마다 ─────→ 평균 · 최대 인원 관측값 + 모니터링 스냅샷(S3) 전송
      └─ 단계 변화 시 ──────→ 연속 프레임 조건(진입 3프레임 · 복귀 5프레임) 충족 시
                              혼잡 시작 / 단계 상승 / 종료 이벤트 + 캡처 이미지 전송
      │
      ▼
BE 서버 : 받은 인원으로 밀도 · 단계를 다시 판정해 DynamoDB에 저장 → 대시보드 실시간 반영
```

#### ③ 대피 경로 탐색 · 재계산 · 유도등 제어

```
[훈련 시작] 시작 노드 → 최종 탈출구 다익스트라 최단 경로 탐색 (화재 구간 제외)
      │
      ▼
혼잡 이벤트 수신 또는 화재 확산 단계 진행
      │
      ▼
엣지 가중치 재계산 : 거리 × 혼잡 배율(CAUTION ×1.5 · CROWDED ×3.0) × 화재 근접 위험 배율
                    VERY_CROWDED · 화재 구간 엣지는 그래프에서 제외
      │
      ▼
우회 경로 산출 → 대시보드에 재탐색 제안(PENDING) 표시
      │
      ├─ 거절 ──────→ 기존 경로 유지
      └─ 승인 ──────→ 출구 기준 역방향 다익스트라로 층 전체 노드의 다음 이동 방향 계산
                      → 유도등별 LEFT / RIGHT 명령 적재
      │
      ▼
Raspberry Pi : 명령 큐 폴링 → 이더넷 릴레이(Modbus TCP)로 좌 · 우 유도등 점등 → ACK 보고
      │
      ▼
관리자 종료 또는 10분 경과 시 훈련 종료
```

#### ④ 훈련 평가 등급 산출

```
[훈련 종료] 관리자 : 실제 대피 완료 인원 입력
      │
      ▼
평가 항목 산출 : 총 대피 시간 · 대피 성공률(생존 인원 ÷ 참여 인원 × 100) · 병목 발생 횟수 · 경로 이탈률
      │
      ▼
가중 합산 : 대피 시간 35% + 대피 성공률 30% + 병목 발생 20% + 경로 이탈률 15% → 100점 만점
      │
      ▼
등급 판정 : A(90점 이상) · B(80~89) · C(70~79) · D(60~69) · F(60점 미만)
      │
      ▼
보고서 생성 : 종합 등급 · 항목별 점수 · 대피 추이 차트 · 강점 / 개선점 · 권고사항 → PDF 다운로드
```



</p>

<br />

## 💡4. 작품 소개영상

> 아래 썸네일을 클릭하면 유튜브에서 Safe Route 시연 영상을 볼 수 있습니다.

[![Safe Route 작품 소개영상](https://github.com/user-attachments/assets/d819da24-21d1-4477-96b9-a7fa6727dcda)](https://youtu.be/mhJJFlJE_6I?si=7cqqasrY9UjTwS1d)


<br />

## 💡5. 핵심 소스코드

#### 5-1. AI · Edge: 밀도 기반 혼잡도 판정 및 혼잡 이벤트 감지
- 소스코드 설명 : Raspberry Pi에서 YOLOv8로 탐지한 ROI 내 인원을 감시 면적으로 나눠 밀도를 구하고, 단계별 임계값으로 혼잡도를 판정합니다. 오탐을 막기 위해 연속 프레임 조건을 만족할 때만 혼잡 시작·단계 상승·종료 이벤트를 서버로 보냅니다.

```Python
# app.py : 인원 → 밀도 → 혼잡도 → 이벤트
def _process_local_event(self, snapshot, count, now_ms, config):
    density = count / config.monitored_area_m2
    level = config.thresholds.classify(density)
    event_type = self._event_detector.observe(level, now_ms, config.event_detection)
    if event_type is None or not config.training_session_id:
        return
    event = CongestionEvent(
        str(uuid.uuid4()), config.training_session_id, self.cctv_code,
        event_type, now_ms, count, density, level, config.config_version,
    )
    self.delivery_queue.submit_event(EventDelivery(event, snapshot))

# models.py : 서버가 내려준 임계값으로 4단계 판정
def classify(self, density: float) -> CongestionLevel:
    if density >= self.very_crowded_from:
        return CongestionLevel.VERY_CROWDED
    if density >= self.crowded_from:
        return CongestionLevel.CROWDED
    if density >= self.caution_from:
        return CongestionLevel.CAUTION
    return CongestionLevel.NORMAL
```

#### 5-2. AI · 도면 분석: 세그멘테이션 결과를 노드·엣지 그래프로 변환
- 소스코드 설명 : S3에 업로드된 도면을 U-Net으로 분석해 공간 그래프를 만들고, 도면의 실측 크기를 반영해 노드 좌표와 엣지 거리(m)를 계산해 백엔드에 돌려주는 FastAPI 엔드포인트입니다.

```Python
@app.post("/analyze-floorplan", response_model=AnalyzeResponse)
def analyze_floorplan_endpoint(req: AnalyzeRequest):
    original_image = download_image_from_s3(req.image_key)
    # ... U-Net 세그멘테이션 및 공간 그래프 생성
    result = analyze_floorplan(tmp_path, model=_model, device=DEVICE,
                               image_size=req.image_size, mode=ANALYSIS_MODE)
    G = result["G"]

    width_scale = req.real_width_m / req.image_size
    height_scale = req.real_height_m / req.image_size

    edges_out = []
    for u, v, edata in G.edges(data=True):
        dr = G.nodes[u]["row"] - G.nodes[v]["row"]
        dc = G.nodes[u]["col"] - G.nodes[v]["col"]
        distance_m = math.sqrt((dc * width_scale) ** 2 + (dr * height_scale) ** 2)
        edges_out.append(EdgeOut(from_temp_id=str(u), to_temp_id=str(v),
                                 distance=round(distance_m, 3), bidirectional=True))
    ...
```

#### 5-3. BE: 혼잡·화재를 반영한 다익스트라 대피 경로 탐색
- 소스코드 설명 : 시작 노드에서 가장 가까운 최종 탈출구까지 최단 경로를 찾습니다. 엣지 가중치에 혼잡 단계별 배율과 화재 근접 위험 배율을 곱하고, 매우 혼잡하거나 화재로 막힌 엣지는 그래프에서 제외합니다. 같은 입력이면 항상 같은 경로가 나오도록 거리가 같을 때 노드 ID 순으로 꺼냅니다.

```Java
PriorityQueue<NodeDistance> queue = new PriorityQueue<>(QUEUE_ORDER);
queue.add(new NodeDistance(startNodeId, 0.0));
Set<UUID> visited = new HashSet<>();

while (!queue.isEmpty()) {
    NodeDistance current = queue.poll();
    if (!visited.add(current.nodeId())) {
        continue;
    }

    MapNode currentNode = nodeById.get(current.nodeId());
    if (currentNode.isExitTarget()) {
        return buildRoute(nodeById, previous, distance, current.nodeId());
    }

    for (MapEdge edge : adjacency.getOrDefault(current.nodeId(), Collections.emptyList())) {
        UUID neighbor = edge.getToNode().getId().equals(current.nodeId())
                ? edge.getFromNode().getId()
                : edge.getToNode().getId();

        double walked = walkedMeters.get(current.nodeId()) + edge.getDistance();
        double arrivalSec = walked / FireProximity.WALKING_SPEED_MPS;
        double newDistance = distance.get(current.nodeId())
                + calculateWeight(edge, weightMultipliers, fireProximity, arrivalSec);
        if (newDistance < distance.getOrDefault(neighbor, Double.MAX_VALUE)) {
            distance.put(neighbor, newDistance);
            walkedMeters.put(neighbor, walked);
            previous.put(neighbor, current.nodeId());
            queue.add(new NodeDistance(neighbor, newDistance));
        }
    }
}
throw new ApiException(EvacuationErrorCode.EVACUATION_ROUTE_NOT_FOUND);

private double calculateWeight(MapEdge edge, Map<UUID, Double> weightMultipliers,
        FireProximity fireProximity, Double arrivalSec) {
    return edge.getDistance()
            * weightMultipliers.getOrDefault(edge.getId(), 1.0)   // CAUTION ×1.5, CROWDED ×3.0
            * fireProximity.multiplier(edge.getId(), arrivalSec);  // 화재 근접 위험 배율
}
```

#### 5-4. IoT: 유도등 제어 명령 폴링 · 릴레이 제어 · ACK 보고
- 소스코드 설명 : 서버(EC2)가 사설망의 Pi를 직접 호출할 수 없기 때문에, Pi가 서버의 유도등 명령 큐를 주기적으로 조회해 방향에 맞는 릴레이 채널을 켜고 실행 결과를 ACK로 보고합니다.

```Python
def poll_once(self) -> int:
    commands = self._client.fetch_light_commands(self._cctv_code)
    for command in commands:
        self._execute_and_ack(command)
    return len(commands)

def _execute_and_ack(self, command: dict) -> None:
    command_id = command.get("commandId")
    direction = command.get("direction")
    try:
        self._apply(direction)
    except (RelayControllerError, ValueError) as exc:
        self._client.ack_light_command(command_id, success=False, fail_reason=str(exc))
        return
    self._client.ack_light_command(command_id, success=True)

def _apply(self, direction: Optional[str]) -> None:
    if direction == "LEFT":
        self._relay.switch_to(LEFT_CHANNEL)
    elif direction == "RIGHT":
        self._relay.switch_to(RIGHT_CHANNEL)
    elif direction == "OFF":
        self._relay.all_off()
    elif direction == "BOTH":
        self._relay.both_on()
    else:
        raise ValueError(f"알 수 없는 유도등 방향: {direction}")
```

#### 5-5. FE: 훈련 세션 실시간 이벤트 구독 (STOMP WebSocket)
- 소스코드 설명 : JWT로 STOMP 서버에 연결해 진행 중인 훈련 세션의 토픽을 구독합니다. 상태 변경이나 경로 차단 이벤트가 오면 관련 쿼리를 무효화해 대시보드를 최신 상태로 갱신하고, 경로 재탐색 제안 등은 화면에 바로 전달합니다.

```TypeScript
const client = new Client({
  brokerURL: `${wsBaseUrl}/ws`,
  connectHeaders: { Authorization: `Bearer ${accessToken}` },
  reconnectDelay: 5_000,
  heartbeatIncoming: 10_000,
  heartbeatOutgoing: 10_000,
  onConnect: () => {
    client.subscribe(`/topic/training-sessions/${sessionId}`, (message) => {
      const event = JSON.parse(message.body) as TrainingSessionEvent;
      if (event.sessionId !== sessionId) return;

      // 상태 변경·경로 차단 시 훈련 상태를 다시 조회
      if (
        event.eventType === TRAINING_EVENT_TYPE.STATUS_UPDATED ||
        event.eventType === TRAINING_EVENT_TYPE.EVACUATION_ROUTE_BLOCKED
      ) {
        void queryClient.invalidateQueries({
          queryKey: dashboardQueryKeys.trainingStatus(sessionId),
        });
      }

      onEventRef.current?.(event);
    });
  },
});

client.activate();
return () => void client.deactivate();
```

<br />
<br />

<p align="center">
  <img width="900" alt="Safe Route 배너" src="https://github.com/user-attachments/assets/0c3e869f-591b-4b07-9403-a91b2c09c360" />
</p>

<br />

<div align="center">
  <strong>관찰을 넘어, 대응하는 대피 훈련으로, Safe Route</strong>
</div>

