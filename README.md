<sub>2026 한이음 드림업 · 26_HF034 · Team 데드락</sub>

# Safe Route <img width="110" align="left" alt="SafeRoute 로고" src="https://github.com/user-attachments/assets/ae3ee84e-ef09-4d46-a864-c0243c664cb9" />

<!-- **관찰을 넘어, 대응하는 대피 훈련으로** -->

![SafeRoute](https://img.shields.io/badge/Safe%20Route-AI%C2%B7IoT%20%EA%B8%B0%EB%B0%98%20%EC%8B%A4%EC%8B%9C%EA%B0%84%20%ED%99%94%EC%9E%AC%20%EB%8C%80%ED%94%BC%20%ED%9B%88%EB%A0%A8%20%EA%B4%80%EB%A6%AC%20%ED%94%8C%EB%9E%AB%ED%8F%BC-DBEAFE?style=for-the-badge&labelColor=2563EB)

 <br/>
 
<p>
  <img alt="엣지 AI 혼잡도 감지" src="https://img.shields.io/badge/%EC%97%A3%EC%A7%80%20AI%20%ED%98%BC%EC%9E%A1%EB%8F%84%20%EA%B0%90%EC%A7%80-E5E7EB?style=flat" />
  <img alt="실시간 대피 경로 재계산" src="https://img.shields.io/badge/%EC%8B%A4%EC%8B%9C%EA%B0%84%20%EB%8C%80%ED%94%BC%20%EA%B2%BD%EB%A1%9C%20%EC%9E%AC%EA%B3%84%EC%82%B0-E5E7EB?style=flat" />
  <img alt="IoT 유도등 방향 제어" src="https://img.shields.io/badge/IoT%20%EC%9C%A0%EB%8F%84%EB%93%B1%20%EB%B0%A9%ED%96%A5%20%EC%A0%9C%EC%96%B4-E5E7EB?style=flat" />
  <img alt="훈련 평가 보고서" src="https://img.shields.io/badge/%ED%9B%88%EB%A0%A8%20%ED%8F%89%EA%B0%80%20%EB%B3%B4%EA%B3%A0%EC%84%9C-E5E7EB?style=flat" />
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
- 프로젝트 명 : [Safe Route] AI·IoT 기반 실시간 화재 훈련 대피 관리 플랫폼
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
| 훈련&nbsp;시작 | 발화 위치·시작 노드 지정 → 화재 회피 최단 경로 탐색 (위험 가중 다익스트라) → 도면 위 기본 경로와 유도등 초기 방향 표시 |
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

#### 대피 경로 탐색 · 재계산 · 유도등 제어

```
[훈련 시작] 시작 노드 → 최종 탈출구 위험 가중 다익스트라 최단 경로 탐색 (화재 구간 제외)
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
      └─ 승인 ──────→ 출구 기준 위험 가중 다익스트라로 층 전체 노드의 다음 이동 방향 계산
                      → 유도등별 LEFT / RIGHT 명령 적재
      │
      ▼
Raspberry Pi : 명령 큐 폴링 → 이더넷 릴레이(Modbus TCP)로 좌 · 우 유도등 점등 → ACK 보고
      │
      ▼
관리자 종료 또는 10분 경과 시 훈련 종료
```


<br />

## 💡4. 작품 소개영상

> 아래 썸네일을 클릭하면 유튜브에서 Safe Route 시연 영상을 볼 수 있습니다.

[![Safe Route 작품 소개영상](https://github.com/user-attachments/assets/d819da24-21d1-4477-96b9-a7fa6727dcda)](https://youtu.be/mhJJFlJE_6I?si=7cqqasrY9UjTwS1d)


<br />

## 💡5. 핵심 소스코드

#### 5-1. AI · Edge : RTSP 영상 수신 및 Hailo 기반 사람 탐지
> RTSP 영상 수신 → **Hailo NPU 추론** → 인원 집계 → 밀도 기반 혼잡도 판단 → 서버 전송

- 소스코드 설명 : IP 카메라의 RTSP 영상을 프레임 단위로 받고, 끊기면 지수 백오프로 재연결합니다. 받은 프레임은 Raspberry Pi 5의 Hailo-8L NPU에서 YOLOv8로 추론해 사람만 골라냅니다.

**IP 카메라 연동 : RTSP 영상 수신**
```Python
class RtspVideoSource(VideoSource):
    def __init__(self, url: str, max_reconnects: int = 5, base_delay_sec: float = 1.0,
                 max_delay_sec: float = 30.0, capture_factory: Optional[Callable] = None,
                 sleeper: Callable[[float], None] = time.sleep) -> None:
        if max_reconnects < 0:
            raise ValueError("max_reconnects must not be negative")
        self.url = url
        self.max_reconnects = max_reconnects
        self.base_delay_sec = base_delay_sec
        self.max_delay_sec = max_delay_sec
        self._capture_factory = capture_factory or _opencv_capture
        self._sleep = sleeper
        self._cap = self._capture_factory(url)

    def frames(self) -> Iterator[object]:
        reconnects = 0
        while self._cap is not None:
            ok, frame = self._cap.read() if self._cap.isOpened() else (False, None)
            if ok:
                reconnects = 0
                yield frame
                continue
            if reconnects >= self.max_reconnects:
                # 정상 종료와 구분해야 systemd 같은 감독자가 프로세스를 다시 띄운다.
                raise RtspStreamLostError(f"RTSP reconnect limit reached ({self.max_reconnects})")
            delay = min(self.base_delay_sec * (2 ** reconnects), self.max_delay_sec)
            reconnects += 1
            logger.warning("RTSP read failed; reconnect %d/%d in %.1fs", reconnects, self.max_reconnects, delay)
            self._sleep(delay)
            self._cap.release()
            self._cap = self._capture_factory(self.url)
```

**Hailo 기반 사람 탐지**
```Python
def detect(self, frame) -> list[Detection]:
    if self._closed:
        raise HailoRuntimeError("Hailo detector가 이미 종료되었습니다.")
    if (
        not isinstance(frame, np.ndarray)
        or frame.ndim != 3
        or frame.shape[2] != 3
        or frame.shape[0] <= 0
        or frame.shape[1] <= 0
        or frame.dtype != np.uint8
    ):
        raise ValueError(
            "frame must be a non-empty uint8 BGR ndarray with shape (H, W, 3)"
        )

    original_height, original_width = frame.shape[:2]
    prepared, scale, pad_x, pad_y = self._preprocess(frame)
    class_outputs = self._runtime.infer(prepared)
    return self._person_detections(
        class_outputs,
        original_width,
        original_height,
        scale,
        pad_x,
        pad_y,
    )
```

#### 5-2. AI · Edge : ROI 인원 집계 및 밀도 기반 혼잡도 판단
> RTSP 영상 수신 → Hailo NPU 추론 → **인원 집계 → 밀도 기반 혼잡도 판단** → 서버 전송

- 소스코드 설명 : 탐지 결과 중 감시 구역(ROI) 안의 인원만 집계합니다. 인원수는 5 FPS로 지속 계산하며, 관측 결과는 1초 주기로 서버에 전송합니다. 밀도는 서버가 내려준 임계값으로 정상·주의·혼잡·매우 혼잡 4단계로 판정합니다.

**(ROI) 인원 집계**
```Python
def process_frame(self, frame, captured_at_ms: Optional[int] = None) -> Optional[CongestionObservation]:
    config = self._config
    if config is None or not config.training_active or not config.training_session_id:
        return None
    self._ensure_delivery_session(config.training_session_id)
    captured_at_ms = self._epoch_ms() if captured_at_ms is None else captured_at_ms
    try:
        detections = self.detector.detect(frame)
    except Exception as exc:
        now = self._monotonic()
        if now - self._last_inference_error_log >= 10.0:
            self._last_inference_error_log = now
            logger.error("Person inference failed (further errors suppressed for 10s): %s", type(exc).__name__)
        return None
    height, width = frame.shape[:2]
    inside_detections = self.roi_counter.filter_inside(detections, width, height)
    count = len(inside_detections)
    if self.preview is not None:
        self._preview_stop_requested = not self.preview.show(frame, detections, inside_detections)
    snapshot = Snapshot(frame.copy(), tuple(detections), tuple(inside_detections))
    self._process_local_event(snapshot, count, captured_at_ms, config)
    if self._initial_snapshot_pending:
        # 훈련 활성화 직후 첫 화면은 집계 구간이 끝날 때까지 기다리지 않고 단일 샘플로 바로 보낸다.
        # 이 샘플은 아래 정기 집계에도 그대로 포함된다.
        self._initial_snapshot_pending = False
        self._submit_monitoring(config, WindowSummary(
            captured_at_ms, captured_at_ms, captured_at_ms, 1, float(count), count,
        ), snapshot)
    summary = self.aggregator.add_sample(count, captured_at_ms)
```

**밀도 기반 혼잡도 판단**
```Python
@dataclass(frozen=True)
class CongestionThresholds:
    caution_from: float
    crowded_from: float
    very_crowded_from: float

    def __post_init__(self) -> None:
        if not (0 <= self.caution_from < self.crowded_from < self.very_crowded_from):
            raise ValueError("congestion thresholds must be non-negative and increasing")

    def classify(self, density: float) -> CongestionLevel:
        if density >= self.very_crowded_from:
            return CongestionLevel.VERY_CROWDED
        if density >= self.crowded_from:
            return CongestionLevel.CROWDED
        if density >= self.caution_from:
            return CongestionLevel.CAUTION
        return CongestionLevel.NORMAL
```

#### 5-3. IoT : 유도등 제어 명령 및 릴레이 제어
> 서버 명령 조회 → **방향 판별 → 릴레이 제어** → 유도등 점등 → 실행 결과 전송

- 소스코드 설명 : 백엔드는 유도등 상태와 설정을 검증한 뒤 방향 명령을 큐에 적재하고, 상태 변경 이벤트를 발행합니다. Pi는 명령을 받아 이더넷 릴레이 채널을 제어하며, 좌·우 채널이 동시에 켜지지 않도록 인터록을 둡니다.

**유도등 제어 명령**
```Java
public LightDirectionResponse changeDirection(
        UUID lightId, ChangeLightDirectionRequest request, String email) {
    IoTLight light = findLightForSchoolOrThrow(lightId, email);
    return changeDirection(light, request);
}

private LightDirectionResponse changeDirection(
        IoTLight light, ChangeLightDirectionRequest request) {
    IoTLightDirection direction = request.direction();

    if (!light.isEnabled()) {
        throw new ApiException(IoTLightErrorCode.LIGHT_DISABLED);
    }
    if (direction != IoTLightDirection.OFF && !light.isGuidanceConfigured()) {
        throw new ApiException(IoTLightErrorCode.GUIDANCE_NOT_CONFIGURED);
    }
    if (light.getCctv() == null) {
        throw new ApiException(IoTLightErrorCode.CCTV_NOT_ASSIGNED);
    }

    enqueueCommand(light, direction);
    iotLightDirectionStore.update(light.getId(), direction);
    Instant changedAt = Instant.now();
    logDirectionChange(light, direction, changedAt);
    trainingEventPublisher.publishIoTLightStatusUpdatedAfterCommit(light, direction);

    return new LightDirectionResponse(light.getId(), direction, changedAt);
}
```

**릴레이 제어**
```Python
def turn_on(self, channel: RelayChannel) -> None:
    """지정한 채널만 켠다.

    반대 채널이 실제로 ON 상태로 확인되면 BothChannelsOnError를 던지고
    아무 명령도 보내지 않는다. 방향을 전환하려면 switch_to()를 사용할 것.
    """
    with self._lock:
        other = self._other_channel(channel)
        if self._read_channel(other):
            raise BothChannelsOnError(
                f"{other.name}가 이미 ON 상태입니다. "
                f"{channel.name}을 켜려면 먼저 {other.name}을 끄거나 switch_to()를 사용하세요."
            )
        self._write_channel(channel, True)

def turn_off(self, channel: RelayChannel) -> None:
    """지정한 채널만 끈다. (OFF는 인터록 대상이 아니므로 항상 허용)"""
    with self._lock:
        self._write_channel(channel, False)

def switch_to(self, channel: RelayChannel) -> None:
    """반대 채널을 끄고 지정한 채널을 켠다. 좌/우 방향 전환에 사용."""
    with self._lock:
        other = self._other_channel(channel)
        self._write_channel(other, False)
        self._write_channel(channel, True)
```

#### 5-4. FE : 훈련 세션 실시간 이벤트 구독 (STOMP WebSocket)
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
  <strong>관찰을 넘어 대응하는 대피 훈련으로, Safe Route</strong>
</div>

