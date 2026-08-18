# Call Me Baby

> 부모와 아이의 일상을 연결하는 AI 기반 실시간 영상통화 서비스

<p align="center">
  <img src="../docs/assets/logo-placeholder.svg" alt="Call Me Baby" width="280" />
</p>

<p align="center"><strong>아이의 오늘을 듣고, 이해하고, 함께 기록하는 AI 육아 동반자</strong></p>

---

## 📌 목차

- [Call Me Baby](#call-me-baby)
  - [📌 목차](#-목차)
  - [🍼 서비스 소개](#-서비스-소개)
  - [💡 기획 배경](#-기획-배경)
  - [📋 프로젝트 개요](#-프로젝트-개요)
  - [👥 팀원 소개](#-팀원-소개)
  - [✨ 주요 기능](#-주요-기능)
    - [👨‍👩‍👧 부모·아이 실시간 영상통화](#-부모아이-실시간-영상통화)
    - [💬 AI 대화 주제 추천](#-ai-대화-주제-추천)
    - [🎨 부모·아이 공동 그림판](#-부모아이-공동-그림판)
    - [📝 통화 후 AI 일기](#-통화-후-ai-일기)
    - [👶 아이 프로필 및 관심사 관리](#-아이-프로필-및-관심사-관리)
    - [🔐 소셜 로그인](#-소셜-로그인)
  - [🎬 시연 영상](#-시연-영상)
  - [🛠 기술 스택](#-기술-스택)
  - [🏗 시스템 아키텍처](#-시스템-아키텍처)
  - [🗄 ERD](#-erd)
  - [📡 API 명세](#-api-명세)
  - [🔬 핵심 기술 상세](#-핵심-기술-상세)
    - [실시간 통화와 AI 음성 분석 분리](#실시간-통화와-ai-음성-분석-분리)
    - [LiveKit 기반 공동 그림판](#livekit-기반-공동-그림판)
    - [아동 음성 특화 STT 모델 파인튜닝](#아동-음성-특화-stt-모델-파인튜닝)
    - [실시간 관심사 분석 파이프라인](#실시간-관심사-분석-파이프라인)
    - [근거 기반 그림일기 생성 파이프라인](#근거-기반-그림일기-생성-파이프라인)
    - [인증 및 연결 보안](#인증-및-연결-보안)
  - [📚 프로젝트 산출물](#-프로젝트-산출물)
  - [📝 회고](#-회고)

## 🍼 서비스 소개

**Call Me Baby**는 부모와 아이가 안전하고 즐겁게 소통할 수 있도록 돕는 AI 기반 실시간 영상통화 서비스입니다.

영상통화 중 아이의 음성을 실시간으로 분석해 대화 주제를 파악하고, 대화를 이어갈 수 있는 질문과 반응을 제공합니다. 통화가 끝나면 AI가 대화 내용을 바탕으로 일기를 생성하고, 부모와 아이가 함께 그린 그림과 메모를 하나의 기록으로 남깁니다.

## 💡 기획 배경

영상통화는 멀리 있는 부모와 아이를 연결하지만, 대화 주제를 찾고 아이의 하루를 꾸준히 기록하는 일은 쉽지 않습니다. Call Me Baby는 대화 소재 부족, 아이의 관심사를 놓치는 문제, 통화 후 기록의 어려움, 함께할 활동 부족을 해결하는 것을 목표로 합니다.

## 📋 프로젝트 개요

| 항목 | 내용 |
| --- | --- |
| 프로젝트명 | Call Me Baby |
| 프로젝트 유형 | AI 기반 부모·아이 실시간 영상통화 서비스 |
| 개발 기간 | `2026.07.06 ~ 2026.08.10` |
| 개발 인원 | 6명 |
| 플랫폼 | Web Application |
| 배포 환경 | Vercel, AWS EC2, GCP GPU Server |

## 👥 팀원 소개


<table>
  <tr>
    <td align="center" valign="top" width="33%" height="320">
      <img src="../docs/assets/team/hyunjee-square.png" alt="강현지 프로필" width="140" height="140" /><br />
      <strong>강현지</strong><br />팀장 · AI<br />
      <a href="https://github.com/hyunjeekang">@hyunjeekang</a><br /><br />
      아동 특화 STT 모델 파인튜닝·서빙<br />실시간 관심사 분석·AI 그림일기 파이프라인<br />&nbsp;
    </td>
    <td align="center" valign="top" width="33%" height="320">
      <img src="../docs/assets/team/LeeEojin-square.png" alt="이어진 프로필" width="140" height="140" /><br />
      <strong>이어진</strong><br />BE · AI<br />
      <a href="https://github.com/">@win929</a><br /><br />
      소셜 로그인·JWT 인증 구현<br />LiveKit 통화 세션·Redis TTL 기반 재접속 복구<br />AI 그림일기 품질 평가·프롬프트 개선
    </td>
    <td align="center" valign="top" width="33%" height="320">
      <img src="https://github.com/wo-oaw.png" alt="임건애 프로필" width="140" height="140" /><br />
      <strong>임건애</strong><br />Infra, BE<br />
      <a href="https://github.com/wo-oaw">@wo-oaw</a><br /><br />
      Jenkins 기반 CI/CD·배포 인프라 구축<br />통화방·Redis 상태관리·그림일기 API<br />&nbsp;
    </td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%" height="320">
      <img src="../docs/assets/team/parkkyuyeon-square.png" alt="박규연 프로필" width="140" height="140" /><br />
      <strong>박규연</strong><br />FE<br />
      <a href="https://github.com/">@babagyuya</a><br /><br />
      주요 페이지 UI/UX 구현<br />소셜 로그인 연동<br />&nbsp;
    </td>
    <td align="center" valign="top" width="33%" height="320">
      <img src="../docs/assets/team/kimsujin.png" alt="김수진 프로필" width="140" height="140" /><br />
      <strong>김수진</strong><br />FE<br />
      <a href="https://github.com/soo83705-ui">@soo83705-ui</a><br /><br />
      FE 영상통화<br />FE 동물필터 성능 개선<br />&nbsp;
    </td>
    <td align="center" valign="top" width="33%" height="320">
      <img src="../docs/assets/team/hyunmin.png" alt="오현민 프로필" width="140" height="140" /><br />
      <strong>오현민</strong><br />FE<br />
      <a href="https://github.com/">@github-id</a><br /><br />
      WebRTC·MediaPipe 기반 실시간 미디어 기능 구현<br />UI/UX 설계<br />&nbsp;
    </td>
  </tr>
</table>

## ✨ 주요 기능

### 👨‍👩‍👧 부모·아이 실시간 영상통화

> 부모와 아이가 하나의 통화방에 입장해 영상과 음성으로 실시간 소통할 수 있습니다. 통화방 생성부터 입장, 재접속, 종료까지의 상태를 안정적으로 관리합니다.

| 통화 화면 | 통화 흐름 GIF |
| --- | --- |
| <img src="../docs/assets/통화 화면.png"> | <img src="../docs/assets/통화 흐름.gif"> |

### 💬 AI 대화 주제 추천

> 아이의 음성을 실시간으로 분석해 관심사를 파악하고, 부모가 자연스럽게 대화를 이어갈 수 있도록 맞춤형 질문과 대화 소재를 제공합니다.

| 대화 주제 추천 화면 | AI 분석 GIF |
| --- | --- |
| <img src="../docs/assets/대화 주제 추천 화면.png"> | <img src="../docs/assets/대화 추천 AI.gif"> |

### 🎨 부모·아이 공동 그림판

> 영상통화 중 부모와 아이가 하나의 캔버스에서 함께 그림을 그립니다. 실시간으로 전달된 그림을 통화 후 기록에 저장해 대화의 추억으로 남길 수 있습니다.

| 공동 그림판 화면 | 그림판 동작 GIF |
| --- | --- |
| <img src="../docs/assets/공동 그림판 화면.png"> | <img src="../docs/assets/그림판 동작.gif"> |

### 📝 통화 후 AI 일기

> 통화 내용을 바탕으로 아이가 들려준 이야기와 부모가 관찰한 모습을 요약해 일기로 생성합니다. 부모 메모와 공동 그림을 함께 확인하고 기록할 수 있습니다.

| AI 일기 화면 | 일기 생성 GIF |
| --- | --- |
| <img src="../docs/assets/AI 일기 화면.png"> | <img src="../docs/assets/일기 생성.gif"> |

### 👶 아이 프로필 및 관심사 관리

> 아이의 프로필과 관심사를 등록하고, 통화 기록과 AI 분석 결과를 아이별로 관리할 수 있습니다.

| 아이 프로필 화면 | 관심사 관리 GIF |
| --- | --- |
| <img src="../docs/assets/아이 프로필 화면.png"> | <img src="../docs/assets/관심사 관리.gif"> |

### 🔐 소셜 로그인

> 카카오·네이버·구글 OAuth를 이용해 간편하게 로그인하고, Access Token과 Refresh Token 기반으로 세션을 안전하게 관리합니다.

| 로그인 화면 | 로그인 GIF |
| --- | --- |
| `[화면 추가 예정]` | `[GIF 추가 예정]` |

## 🎬 시연 영상

> 전체 서비스 흐름 영상과 기능별 GIF는 추후 추가 예정입니다.

| 구분 | 자료 |
| --- | --- |
| 전체 시연 영상 | `[YouTube 또는 Google Drive 링크 추가 예정]` |
| 로그인 및 아이 등록 | `[GIF 추가 예정]` |
| 통화방 생성 및 입장 | `[GIF 추가 예정]` |
| AI 대화 주제 추천 | `[GIF 추가 예정]` |
| 공동 그림판 | `[GIF 추가 예정]` |
| 통화 후 AI 일기 | `[GIF 추가 예정]` |

## 🛠 기술 스택

| 분류 | 기술 |
| --- | --- |
| **Frontend** | <img src="https://img.shields.io/badge/React-18.3.1-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React 18.3.1" /> <img src="https://img.shields.io/badge/TypeScript-5.6.3-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript 5.6.3" /> <img src="https://img.shields.io/badge/React_Router-6.30.4-CA4245?style=for-the-badge&logo=reactrouter&logoColor=white" alt="React Router 6.30.4" /> <img src="https://img.shields.io/badge/Vite-6.4.3-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite 6.4.3" /> <img src="https://img.shields.io/badge/MediaPipe_Tasks_Vision-1.0.0-0097A7?style=for-the-badge&logo=mediapipe&logoColor=white" alt="MediaPipe Tasks Vision 1.0.0" /> |
| **Backend** | <img src="https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 21" /> <img src="https://img.shields.io/badge/Spring%20Boot-4.1.0-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot" /> <img src="https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white" alt="Spring Data JPA" /> <img src="https://img.shields.io/badge/Spring%20Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white" alt="Spring Security" /> <img src="https://img.shields.io/badge/OAuth%202.0-3C3C3C?style=for-the-badge&logo=oauth&logoColor=white" /> <img src="https://img.shields.io/badge/Resource%20Server-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white" /> <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white" />
| **Database** | <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL" /> <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis" /> <img src="https://img.shields.io/badge/Flyway-CC0200?style=for-the-badge&logo=flyway&logoColor=white" alt="Flyway" /> |
| **AI · STT** | <img src="https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.11" /> <img src="https://img.shields.io/badge/FastAPI-0.140.13-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI 0.140.13" /> <img src="https://img.shields.io/badge/PyTorch-2.11.0-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch 2.11.0" /> <img src="https://img.shields.io/badge/Transformers-5.14.1-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="Transformers 5.14.1" /> <img src="https://img.shields.io/badge/PEFT-LoRA-FF9D00?style=for-the-badge" alt="PEFT LoRA" /> <img src="https://img.shields.io/badge/Whisper-small%20v2-412991?style=for-the-badge&logo=openai&logoColor=white" alt="Whisper small v2" /> <img src="https://img.shields.io/badge/WebRTC%20VAD-2.0.14-333333?style=for-the-badge&logo=webrtc&logoColor=white" alt="WebRTC VAD 2.0.14" /> |
| **AI · NLP & LLM** | <img src="https://img.shields.io/badge/Kiwi-0.23.2-F5A623?style=for-the-badge" alt="Kiwi 0.23.2" /> <img src="https://img.shields.io/badge/Sentence%20Transformers-5.6.1-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="Sentence Transformers 5.6.1" /> <img src="https://img.shields.io/badge/multilingual--e5--small-Embeddings-7B61FF?style=for-the-badge" alt="multilingual-e5-small" /> <img src="https://img.shields.io/badge/GMS%20API-gpt--4.1-412991?style=for-the-badge&logo=openai&logoColor=white" alt="GMS API gpt-4.1" /> |
| **Realtime** | <img src="https://img.shields.io/badge/WebRTC-333333?style=for-the-badge&logo=webrtc&logoColor=white" alt="WebRTC" /> <img src="https://img.shields.io/badge/LiveKit-111111?style=for-the-badge&logo=livekit&logoColor=white" alt="LiveKit" /> <img src="https://img.shields.io/badge/WebSocket-010101?style=for-the-badge&logo=socketdotio&logoColor=white" alt="WebSocket" /> |
| **Infrastructure** | <img src="https://img.shields.io/badge/AWS%20EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white" alt="AWS EC2" /> <img src="https://img.shields.io/badge/GCP%20GPU%20Server-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white" /> <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/Docker%20Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker Compose" /> <img src="https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white"> <img src="https://img.shields.io/badge/Caddy-1F88C0?style=for-the-badge&logo=caddy&logoColor=white" alt="Caddy" /> <img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Vercel" /> <img src="https://img.shields.io/badge/GitLab%20Webhook-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white"> |
| **Storage & Tools** | <img src="https://img.shields.io/badge/Amazon%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white" alt="Amazon S3" /> <img src="https://img.shields.io/badge/OpenAPI-6BA539?style=for-the-badge&logo=swagger&logoColor=white" alt="OpenAPI" /> <img src="https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white" alt="Postman" /> |

## 🏗 시스템 아키텍처

![Call Me Baby 시스템 아키텍처](../docs/assets/system-architecture.png)

- **Frontend**: React + TypeScript + Vite, Vercel 배포
- **Application Server**: AWS EC2 Docker Compose 환경의 Caddy, LiveKit, Spring Boot, MySQL, Redis
- **Real-time Media**: LiveKit Self-hosted SFU를 통한 WebRTC 전달
- **STT Server**: GCP GPU 서버의 LiveKit Agent + WebRTC VAD + Transformers FP16 기반 아동 특화 Whisper-small v2
- **AI Pipeline**: Kiwi + 문맥 N-gram + multilingual-e5-small 관심사 분석, GMS API `gpt-4.1` 기반 그림일기 생성
- **Object Storage**: Amazon S3 그림 저장

## 🗄 ERD

![Call Me Baby ERD](../docs/assets/erd.png)

| 도메인 | 주요 테이블 | 설명 |
| --- | --- | --- |
| 인증 | `social_accounts`, `refresh_tokens` | 소셜 계정과 토큰 |
| 사용자 | `parents`, `children` | 부모 계정과 아이 프로필 |
| 관심사 | `interests`, `child_interests` | 관심사 마스터와 분석 결과 |
| 통화 | `call_rooms` | 통화방 상태·시작·종료 |
| 기록 | `diaries` | AI 일기·부모 메모·그림 |

## 📡 API 명세

- [REST API OpenAPI](../docs/api/openapi.yaml)
- [API 안내](../docs/api/README.md)
- [실시간 통신 계약](../docs/realtime/REALTIME_CONTRACT.md)
- [내부 AI API](../docs/api/ai-internal-openapi.yaml)
- [내부 Realtime API](../docs/api/realtime-internal-openapi.yaml)
- [Postman 테스트 문서](../docs/postman/README.md)

| 영역 | 대표 기능 |
| --- | --- |
| 인증 | OAuth 로그인, 토큰 재발급, 로그아웃 |
| 아이 | 아이 등록·조회·수정·삭제 |
| 관심사 | 관심사 및 아이 관심사 조회 |
| 통화방 | 생성, 입장 토큰, 상태 조회·종료 |
| 일기 | 목록·상세 조회, AI 일기 재생성 |

## 🔬 핵심 기술 상세

### 실시간 통화와 AI 음성 분석 분리

LiveKit을 미디어 전달 계층으로 사용하고 STT Agent는 아이의 microphone track만 선택 구독하도록 구성했습니다. 통화 품질과 AI 분석 처리를 분리해 통화 흐름에 미치는 영향을 줄였습니다.

### LiveKit 기반 공동 그림판

| 기술                           | 선택 및 활용 이유                                                    |
| :--------------------------- | :------------------------------------------------------------ |
|   React                      | 컴포넌트와 상태 기반으로 영상통화·그림판 UI를 구성하고 LiveKit과 연동하기 위해 사용           |
|   TypeScript                 | 그림판 이벤트, 참가자 상태, 실시간 메시지 구조를 타입으로 관리해 오류 가능성을 줄이기 위해 사용       |
|   Vite                       | React SPA의 빠른 개발 환경과 ESM 기반 빌드 환경을 구성하기 위해 사용                 |
|   LiveKit Client             | WebRTC 영상통화와 Data Packet 기반 실시간 데이터 통신을 하나의 Room에서 처리하기 위해 사용 |
|   LiveKit Components React   | LiveKit의 Room·Participant·Track 상태를 React 컴포넌트와 연동하기 위해 사용    |


LiveKit Data Packet을 활용해 별도의 WebSocket 서버 없이 영상통화에 참여한 부모와 아이의 그림판을 실시간으로 동기화했습니다.

| 핵심 구현           | 적용 내용                                                        |
| :-------------- | :----------------------------------------------------------- |
|   데이터 전송 분리     | 그림 선은 안정적인 전달을, 커서는 빠른 반응성을 우선하도록 데이터 특성에 따라 전송 방식을 분리       |
|   좌표 정규화        | 픽셀 좌표가 아닌 캔버스 비율 좌표를 사용해 서로 다른 화면 크기에서도 동일한 위치에 그림이 표시되도록 구현 |
|   선 데이터 묶음 전송   | 연속적으로 발생하는 선 데이터를 묶어 전송해 메시지 수와 통신량을 감소                      |
|   재접속 상태 복구     | 연결 중단이나 새로고침 시 버전 기반 스냅샷을 비교해 최신 그림을 복구하고 양쪽 화면의 상태를 다시 동기화  |

---

### MediaPipe 기반 동물 얼굴 필터

| 기술                         | 선택 및 활용 이유                                                       |
| :------------------------- | :--------------------------------------------------------------- |
|   React                    | 영상통화 화면과 동물 필터의 상태를 컴포넌트 단위로 관리하기 위해 사용                          |
|   TypeScript               | 얼굴 랜드마크, 필터 상태, 영상별 추론 상태를 타입으로 관리해 런타임 오류 가능성을 줄이기 위해 사용        |
|   Vite                     | MediaPipe WASM을 사용하는 브라우저 기반 React 애플리케이션의 개발·빌드 환경으로 활용         |
|   MediaPipe Tasks Vision   | 별도의 AI 서버 없이 브라우저에서 Face Landmarker를 실행해 실시간 얼굴 랜드마크를 추출하기 위해 사용 |


MediaPipe Face Landmarker를 브라우저에서 실행해 별도의 AI 서버로 영상 프레임을 전송하지 않고 얼굴의 위치·크기·회전을 추적하여 동물 필터를 실시간으로 합성했습니다.

| 핵심 구현            | 적용 내용                                                        |
| :--------------- | :----------------------------------------------------------- |
|   얼굴 랜드마크 추적     | 눈·코·입·얼굴 윤곽 등의 랜드마크를 기반으로 필터의 위치·크기·회전을 계산                   |
|   화면 좌표 보정       | 영상의 좌우 반전과 화면 비율을 보정해 얼굴 움직임에 따라 필터가 자연스럽게 따라가도록 구현          |
|   추론 입력 축소       | 화면에 표시되는 원본 영상은 유지하면서 추론용 입력의 긴 변을 최대 `480px`로 축소해 연산량 감소    |
|   추론 스케줄링        | Local·Remote 영상을 동시에 분석하지 않고 번갈아 추론해 CPU·GPU의 순간적인 연산 부하를 완화 |
|   불필요한 추론 제거     | 새로운 영상 프레임이 없거나 필터를 사용하지 않는 경우 얼굴 추론을 생략                     |
|   GPU → CPU 전환   | GPU 추론이 불가능하거나 오류가 반복되는 환경에서는 CPU 방식으로 전환해 실행 안정성을 확보        |






### 아동 음성 특화 STT 모델 파인튜닝

범용 `openai/whisper-small`에 AI-Hub 아동 음성을 LoRA로 학습했습니다.

| 동일 7–10세 외부 평가 | 기본 Whisper-small | v1 | v2 |
| :---: | :---: | :---: | :---: |
| 학습 데이터 | - | 7–10세 15시간 | 7–10세 15시간 + 3–6세 15시간 |
| CER | 13.22% | 8.98% | **8.65%** |

동일한 7–10세 외부 평가에서 Whisper-small 대비 v2의 CER를 13.22%에서 8.65%로 **상대 34.6% 개선**했습니다. 또한 3–6세 데이터를 추가한 v2에서도 기존 7–10세 성능을 유지·개선해 연령 확장에 따른 성능 저하를 방지했습니다. 최종 모델은 GCP GPU 서버에서 Transformers FP16 기반 실시간 STT API로 적용했습니다.

### 실시간 관심사 분석 파이프라인

아이 STT를 Kiwi 직접·별칭 매칭, 문맥 N-gram, 카탈로그-`multilingual-e5-small` 의미 검색 순으로 분석합니다. 관심사 카탈로그는 `2019 개정 누리과정`, `2022 개정 초등학교 교육과정`, `어린이 미디어 이용 조사`를 참고해 서비스용으로 구성하고, AI-Hub 3–7세 자유대화 라벨 11,467건으로 실제 어휘와 별칭을 보강했습니다.

```text
확정 CHILD STT
  → Kiwi 직접 매칭 → 문맥 N-gram → E5 의미 검색
  → 부정·중복·쿨다운 필터링
  → Redis 세션 누적 → SSE 토픽 카드 → 후속 질문 3개
```

추천은 직접 매칭 → 문맥 매칭 → 의미 매칭 순으로 우선하며, 통화 후 반복·긍정·부모 선택 근거를 종합해 관심사 후보를 제안합니다.

### 근거 기반 그림일기 생성 파이프라인

통화 종료 후 확정 STT·부모가 선택한 토픽·부모 메모를 근거로 GMS API의 `gpt-4.1`이 그림일기를 생성합니다.

```text
확정 STT + 선택 토픽 + 부모 메모
  → 개인정보 제거·입력 검증
  → CHILD 발화 기반 사건 추출
  → gpt-4.1 그림일기 생성
  → JSON Schema·378자·안전성·발화 근거 검증
  → 실패 시 1회 보정 또는 저장 중단
```

아이 발화에 없는 사실이 추가되지 않도록 문장별 근거를 검증하고, 외부 API 전송 전 개인정보를 마스킹했습니다.

### 인증 및 연결 보안

- Refresh Token은 해시값과 회전·폐기 상태 관리
- LiveKit 토큰에 방 단위 참가 권한과 publish/subscribe 권한 부여
- Caddy를 통한 HTTPS/WSS 통합 라우팅
- 운영 로그에 STT 원문·사용자 이름·토큰 등 민감 정보 미기록

## 📚 프로젝트 산출물

| 산출물 | 링크 |
| --- | --- |
| 요구사항 명세서 | `[링크 추가 예정]` |
| 화면 설계서 | `[링크 추가 예정]` |
| API 명세서 | [OpenAPI](../docs/api/openapi.yaml) |
| ERD | [이미지](../docs/assets/erd.png) |
| 시스템 아키텍처 | [이미지](../docs/assets/system-architecture.png) |
| 시연 시나리오 | [문서](../docs/demo-stt-interest-drawing-scenario.md) |

## 📝 회고

* **잘한 점:**
  기획 단계부터 개발, 사용자 테스트, 최종 발표 준비까지 팀원들과 역할을 나누고 꾸준히 소통하며 프로젝트를 끝까지 완성했다. 특히 부모와 아이의 영상통화라는 핵심 기능에 공동 그림판, 대화 주제 추천, 그림일기 등 다양한 기능을 연결하면서 단순한 영상통화 서비스를 넘어 실제 가족 간 소통에 도움이 되는 서비스로 발전시킬 수 있었다. 개발 과정에서 발생한 기능 오류나 UI/UX 개선 사항도 팀원들과 빠르게 공유하고 수정했으며, 사용자 테스트를 통해 실제 사용자의 반응을 확인하고 이를 최종 서비스와 발표 자료에 반영한 점도 좋았다.

* **아쉬웠던 점:**
  가장 아쉬웠던 부분은 **본 발표에서 실시간 서비스 시연에 실패한 것**이다. 개발 및 사전 테스트 과정에서는 정상적으로 동작했던 기능이었지만, 실제 발표 환경에서는 예상하지 못한 문제가 발생하면서 준비했던 서비스의 주요 기능을 직접 보여주지 못했다. 프로젝트의 완성도와 별개로 발표에서는 짧은 시간 안에 서비스를 안정적으로 전달하는 것 역시 중요하다는 점을 체감했다. 또한 실제 발표 환경과 동일한 네트워크 및 기기 조건에서 조금 더 반복적으로 리허설하고, 실시간 시연이 실패했을 경우 바로 전환할 수 있는 시연 영상이나 대체 시나리오를 더 철저하게 준비했으면 좋았을 것 같다.

* **배운 점과 개선 방향:**
  이번 프로젝트를 통해 서비스를 완성하는 데에는 단순한 기능 구현뿐만 아니라 **사용자 경험, 예외 상황 처리, 서비스 안정성, 발표 환경까지 고려한 전체적인 준비가 필요하다**는 것을 배웠다. 특히 영상통화와 같이 네트워크 상태나 외부 환경의 영향을 많이 받는 기능은 정상 동작만 확인하는 것이 아니라 연결 끊김, 새로고침, 재접속 등 다양한 상황을 미리 고려해야 한다는 것을 경험했다. 앞으로는 개발 단계에서부터 예외 상황과 장애 상황을 더 구체적으로 정의하고 테스트 케이스를 작성하며, 최종 발표 전에는 실제 발표 환경을 기준으로 여러 차례 리허설을 진행할 예정이다. 또한 실시간 시연이 필요한 프로젝트에서는 문제가 발생하더라도 발표 흐름이 끊기지 않도록 **백업 영상과 대체 시연 방법을 함께 준비하는 습관**을 갖고자 한다.

