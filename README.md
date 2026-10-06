<div align="center">

## 이민석 · Lee Minseok

**임베디드에서 서버·배포 웹 개발 파이프라인까지, 시스템의 아래층부터 다양한 범위를 경험한 개발자**

<br/>
원인을 끝까지 확인하고, 같은 문제가 다시 생기지 않도록 검증합니다

</div>

<br/>

### Profile

- **SSAFY 15기** · Python/AIoT 트랙 (2026.01 ~)
- **자격증** · 정보처리기사, SQLD, 한국사능력검정시험 1급
- **어학** · TOEIC Speaking IH

<br/>

### Tech Stack

| 분야 | 기술 |
|:--|:--|
| **Language** | <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/> <img src="https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=black"/> <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black"/> <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white"/> |
| **Web** | <img src="https://img.shields.io/badge/Django%20REST-092E20?style=flat-square&logo=django&logoColor=white"/> <img src="https://img.shields.io/badge/Vue%203-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white"/> |
| **AI · Embedded** | <img src="https://img.shields.io/badge/YOLO-111F68?style=flat-square&logo=ultralytics&logoColor=white"/> <img src="https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white"/> <img src="https://img.shields.io/badge/TensorRT-76B900?style=flat-square&logo=nvidia&logoColor=white"/> <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white"/> <img src="https://img.shields.io/badge/Jetson%20Orin%20Nano-76B900?style=flat-square&logo=nvidia&logoColor=white"/> <img src="https://img.shields.io/badge/Arduino-00878F?style=flat-square&logo=arduino&logoColor=white"/> |
| **Infra · DevOps** | <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/> <img src="https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white"/> <img src="https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white"/> <img src="https://img.shields.io/badge/AWS%20EC2-FF9900?style=flat-square"/> <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white"/> <img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white"/> <img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white"/> <img src="https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white"/> <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black"/> |

<br/>

### Projects

#### SOBI · 소상공인 정책자금 플랫폼
`2026.08 – 2026.09` `6인 팀` `인프라·DevOps 단독` `자격 판정 고도화`

> 팀이 만든 서비스가 올라갈 서버와 배포 파이프라인을 혼자 설계·구축했습니다.

- **서버 구성** — AWS EC2에 컨테이너 7종을 Docker Compose로 구성. 네트워크를 frontend · backend · data · monitoring 4계층으로 나누고 내부망은 외부에서 닿지 않게 설계해, 외부 포트는 22/80/443 세 개만 개방
- **CI/CD** — Jenkins로 master 자동 배포, develop은 배포와 같은 이미지 빌드로 사전 검증. 빌드가 실패하면 배포 단계가 건너뛰어져 운영 서버가 보호되는 구조
- **데이터 · 관측** — PostgreSQL 16(pgvector) · Redis 7 운영, 일일 백업 7일 보관과 별도 DB 복구 리허설, Prometheus · Grafana 모니터링, Let's Encrypt HTTPS
- **배포 사전 점검** — 첫 배포 전 설정 대조로 실패 요인 3건(Java 버전 불일치, context-path 누락, Flyway 설정 위치)을 미리 차단
- **AI 파트 지원** — 공고 API 응답을 전수 확인해 문서에 없는 필드를 찾아, 공고 300건 기준 커버리지 82.7% → 100%

#### 길봄 · 점자블록 파손 탐지 자율주행 순찰 로봇
`2026.07 – 2026.08` `7인 팀` `임베디드팀 팀장`

> 인도를 스스로 주행하며 점자블록 파손을 찾아내는 로봇입니다. 자율주행 로직, 판정 모델, 하드웨어를 맡았습니다.

- **주행 방식 전환** — 야외 햇빛 간섭으로 LiDAR가 주변 전체를 장애물로 인식해 이동이 불가능한 것을 확인하고, 카메라 기반 보도블록 인식 + 코스트맵 조향으로 전환
- **자율주행 로직** — FSM · 조향 · 회피 · 코스트맵 설계, 상태를 14개에서 8개로 정리
- **점자블록 판정 모델** — 실주행에서 가로 블록을 못 잡는 원인이 학습 데이터의 세로 블록 99.3% 편향임을 찾아, 회전 증강 → 웹캠 높이 실사 촬영 → 주행 중 프레임 수집으로 재학습. 주행 시점 mAP50 0.580 → 0.811, 노면 오탐 16.7% → 0%
- **온디바이스 추론** — Jetson Orin Nano에서 ONNX → TensorRT 변환 후 추론
- **하드웨어** — 센서 · 모터 드라이버 배선 설계

#### SSAFY International ERP
`2026.05 – 2026.06` `2인 풀스택` `발표 평가 우수상`

> Django REST Framework + Vue 3 기반 ERP입니다. 두 명이 도메인 단위로 나눠 개발했습니다.

- **담당 도메인** — 구매/BOM · 재고 · 물류 API와 화면, 경영 · 영업 대시보드
- **AI 수요예측** — 희소 구간을 뺀 선형회귀 + 95% 신뢰구간, 학습/검증을 나눈 MAPE 백테스트로 제품별 과잉 · 부족 판단
- **데이터 정합성 검증** — 대시보드 지표 오류 5종(운임을 매출에 합산, 연도를 무시한 월별 집계, 고정 비율 가짜 마진 등)을 찾아 수정
- **기준일(anchor) 패턴** — 시드 데이터가 과거라 '오늘' 기준 필터가 0건이 되는 문제를 데이터셋 최신 시점 기준으로 해결

#### 그 외 프로젝트

| 프로젝트 | 기간 · 팀 | 담당 | 핵심 |
|:--|:--|:--|:--|
| 미세먼지 감지 · 알림 시스템<br/><sub>졸업 캡스톤</sub> | 2024.03 – 06<br/>2인 | 하드웨어 · 서버 · 서버-앱 통신 | Arduino 센서 노드, Python 초안을 C/pthread 멀티스레드 TCP 서버로 재작성 |
| 똑독 · 구독 관리 플랫폼<br/><sub>데이터베이스 과목</sub> | 2023.09 – 12<br/>4인 | 사용자 홈 · 구독 추가 화면 | PHP + MySQL, 중복 구독을 복합 PK와 조회 쿼리 두 층에서 차단 |
| [AI 챌린지 · 분리수거 이미지](https://github.com/leeminseok11/ai_challenge)<br/><sub>SSAFY</sub> | 2026.03<br/>4인 | 학습 모델 개발 | 반 1위 |
