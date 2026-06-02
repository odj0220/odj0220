# 경력
## 피트릭스 (2026.02 ~ 현재)
### 담당업무
개발팀장, 백엔드 · 프론트엔드 전반 관리
### 프로젝트
- Fittrix 스마트미러 측정 서비스 백엔드 (2026.02 ~ 현재)
  * **What:** 스마트미러 기반 체형·체성분 측정 서비스의 멀티 테넌트 API 서버 개발 및 운영
  * **How:**
    + 체형·자세·스크리닝·골프·다이어트 등 도메인별 PDF 리포트 v2 API 신규 설계·런칭 (v2.4 → v2.9 단독 주도)
    + 4개 언어(한/영/일/번체중국어) 다국어 리포트 지원 및 미지원 언어 자동 폴백 구현
    + FootPressure·PelvisTilt·Shoulder·Spine 등 자세 측정 등급 경계값 전면 보정 (round → floor 일관화)
    + 심각도 기반 worst-item 선정 + 예측모델 rank 정렬 기준 재정의로 리포트 추천 정확도 개선
    + Unity 클라이언트와 측정 항목 등급 판정 스펙 통일(SSOT 문서화)
    + GitHub Actions 기반 CI/CD 구축 (Azure Container Apps 자동 배포)
    + Claude API 활용 릴리즈 노트 자동 생성 + GitHub Release 자동 발행
    + MS Teams Adaptive Card 자동 알림 + Notion 배포 이력 자동 기록
    + Claude Code PR 자동 리뷰 도입으로 코드 리뷰 1차 게이트 자동화
    + Admin 구독 관리 시스템 신규 구축 (플랜·미러별 user_count 집계), Stripe 연동
    + 카카오/구글 소셜 로그인 + 비밀번호 재설정 API 구현, 레거시(phone-only) 계정 무중단 연동
    + 파일 백업을 Azure Blob 직통 스트림 업로드로 전환 (디스크 경유 제거)
    + RabbitMQ 재연결 무한 루프 버그 수정, 미사용 BullMQ/Redis/MongoDB 코드 정리
  * **Impact:**
    + 리포트 v2 런칭으로 신규 매출 채널 기반 마련
    + 일본·대만 해외 서비스 확장 기반 확보, 다국어 표시 장애 0건화
    + 클라이언트–서버 등급 불일치 이슈 구조적 제거
    + 수동 배포 프로세스 및 릴리즈 문서화 수작업 제거로 릴리즈 운영 부담 해소
    + 메모리·디스크 부하 감소 및 기술 부채 제거
- Fittrix Admin — 운영 관리자 콘솔 (2026.02 ~ 현재)
  * **What:** 백엔드에 jQuery로 임베디드돼 있던 레거시 관리 화면을 독립 프론트엔드 서버로 분리·재구축
  * **How:**
    + Next.js 15 (App Router) · React 19 기반 독립 콘솔 신규 구축
    + 인증·사이드바 레이아웃·API 클라이언트 구조 설계 (토큰 만료 시 세션 안정화)
    + 테마/모드/버전, 그룹·미러·관리자 계정, QnA·문의, CDN 관리 기능 단독 구현
    + 구독·결제내역 관리 화면 구축 (플랜·미러별 집계, 수기/정기 결제 판단)
    + InvoicePopup 공통 컴포넌트 추출로 타 앱과 재사용
  * **Impact:**
    + jQuery 임베디드 구조 탈피, 독립 서비스로 유지보수성·확장성 확보
    + B2B 과금 운영 화면 일원화
  * **Legacy → Now:** jQuery (백엔드 임베디드) → Next.js 15 · React 19 · TypeScript · Radix UI · Tailwind CSS · i18next
- Fittrix Studio — 센터 운영 대시보드 (2026.02 ~ 현재)
  * **What:** 피트니스 센터 운영자용 회원·검사·결제 관리 대시보드 마이그레이션 및 기능 확장
  * **How:**
    + React 19 + Vite + React Router DOM 기반 앱을 Next.js 15 App Router로 이관
    + react-router-dom 호출을 자체 navigation 호환 레이어로 치환, SSR 환경 하이드레이션 오류 구조적 해소
    + Stripe·TossPayments SDK 연동, 구독 상태 기반 접근 통제 일원화
    + Recharts·커스텀 차트로 누적 검사 추이 시각화 (결측월 라인 끊김·라벨 클리핑 버그 해소)
    + InBody·MBTI Unity WebGL을 postMessage 브릿지로 연동
    + TanStack Query optimistic update로 상태 토글 즉시 반영, queryClient 싱글톤화로 캐싱 버그 제거
  * **Impact:**
    + 레거시 React/Vite 구조를 Next.js 기반으로 현대화, 유지보수성 개선
    + 결제 플로우 통합으로 B2B 구독 과금 체계 정립
  * **Legacy → Now:** React 19 + Vite + React Router DOM → Next.js 15 · TanStack Query · Stripe · TossPayments · Recharts · Radix UI · dnd-kit · Unity WebGL · Tailwind CSS
- Fittrix Report — 측정 리포트 뷰어 (2026.02 ~ 현재)
  * **What:** Vue 기반 레거시 리포트 서비스를 Next.js로 이관하고 리포트 v2 전면 재설계
  * **How:**
    + Vue SFC 26개 + vue-i18n + @coreui/vue-chartjs 구성을 Next.js 15 · react-i18next · react-chartjs-2로 전면 이관 (27개 TSX 변환)
    + 체형·자세·스크리닝·골프·다이어트 등 도메인별 리포트 v2 화면 신규 설계·런칭 (v2.4 → v2.5 단독 주도)
    + Chart.js 레이더 차트를 커스텀 SVG 차트로 대체 (골프 스윙 탄도 등 도메인 특화 시각화)
    + A4 PDF 출력 대응 (iOS Safari 스케일링 이슈 해결, 화면-인쇄 일관성 확보)
    + 4개 언어 리포트 지원, x-language 헤더 전파 + 미지원 locale 자동 폴백
    + PDF 로직을 @fx-fe/report-pdf 공유 패키지로 추출, 사용자 앱과 공용화
  * **Impact:**
    + 리포트 v2 사용자 접점 완성으로 신규 매출 채널 지원
    + 해외(일본·대만) 확장 기반 마련, 다국어 표시 장애 0건화
  * **Legacy → Now:** Vue + vue-i18n + @coreui/vue-chartjs → Next.js 15 · 커스텀 SVG 차트 · react-chartjs-2 · react-i18next · Tailwind CSS
- Fittrix App — 사용자 클라이언트 (2026.02 ~ 현재)
  * **What:** React + Vite 기반 사용자 앱을 Next.js로 마이그레이션하고 소셜 로그인·AI 리포트 진입 흐름 구현
  * **How:**
    + React 19 + Vite + React Router DOM 7 기반 앱을 Next.js 15 App Router로 이관
    + 카카오/구글 OAuth 소셜 로그인 + 비밀번호 재설정 구현 (컨테이너 내부 redirect_uri 문제 해결)
    + 회원가입 전화번호 국가 자동 감지, 카카오 이름·gender fallback 등 가입 실패 요인 저감
    + 구독 여부에 따라 분기되는 AI 리포트 팝업 구현 (Safari 드래그 스크롤 대응)
    + DOMPurify 적용·쿠키 Secure 플래그 등 보안 이슈 정리, Suspense 경계 처리로 prerender 빌드 에러 해소
    + @fx-fe/report-pdf 공유 패키지 연동
  * **Impact:**
    + 레거시 탈피 및 소셜 로그인 도입으로 사용자 접근성·편의성 향상
    + 가입 실패율 저감 및 보안 강화
  * **Legacy → Now:** React 19 + Vite + React Router DOM 7 → Next.js 15 · OAuth(Kakao/Google) · Chart.js · QR Scanner · i18next · Tailwind CSS
- 프론트 공통 인프라 (2026.02 ~ 현재)
  * **What:** 4개 프론트엔드 앱을 통합하는 모노레포 인프라 및 배포 자동화 파이프라인 구축
  * **How:**
    + Turborepo + pnpm 모노레포 통합, 공통 패키지(@fx-fe/ui·utils·report-pdf) 추출
    + GitHub Actions 변경 감지 선택적 빌드 → Azure Container Apps 자동 배포
    + v<버전>-<앱> 태그 트리거 릴리즈, Claude API 릴리즈 노트 자동 생성 + GitHub Release 자동 발행
    + Teams·Notion 배포 자동 기록, Claude Code PR 자동 리뷰
  * **Impact:**
    + 4개 앱 통합 관리로 개발 생산성 및 코드 재사용성 향상
    + 전체 배포 파이프라인 자동화로 릴리즈 운영 부담 제거
## 와그 (2022.09  ~ 2025.05)
### 담당업무
프론트앤드 개발, 웹 팀장
### 프로젝트
- 와그 모던 개발 (2022.09  ~ 2023.06)
    - **What:** 기존 레거시 와그웹을 대체하는 신규 플랫폼 개발  
    - **How:**  
      - 모노레포 아키텍처 설계 및 도입  
      - Next.js + NestJS 기반 프론트/백엔드 개발 총괄  
      - BFF(Backend For Frontend) 아키텍처 적용  
      - AWS, Jenkins, CodeDeploy 기반 CI/CD 구축  
      - GTM 도입 및 마케팅 스크립트 코드 분리  
      - STG 서버 구축 및 Winston 기반 로그 체계 마련  
    - **Impact:**  
      - 웹 성능 지표 및 검색 노출 향상 → 신규 유저 유입 증가
      - 배포 자동화로 개발 생산성 및 운영 안정성 확보
      - 모던 아키텍처 도입으로 장기적 유지보수성·확장성 개선
- 와그 웹 신규기능 추가 및 유지보수 (MAU 100만)
    - **What:** 기존 레거시 사이트를 모던 스택으로 이관하고, 신규 기능을 지속적으로 개발/운영
    - **How:**
        - Next.js Pages Router → App Router 전환 및 마이그레이션 (Next.js 12 → 14 → 15)
        - React 19 업그레이드 및 마이그레이션 수행 (Next.js 14 → 15 전환시 진행)
        - Nginx 기반 무중단 배포 파이프라인 설계 및 운영
        - ELK 스택 도입으로 로그 및 마케팅 데이터 수집 체계 구축
        - 데이터 분석을 위한 대시보드 및 시각화 기능 개발
    - **Impact:** 
        - 모바일 웹 바이탈 점수 90% "나쁨" → 95% "좋음"으로 개선
        - 무중단 배포로 배포 안정성 확보 및 장애 최소화
        - 마케팅 데이터 기반 의사결정 프로세스 고도화
## 골라라 (2021.08  ~ 2022.07)
### 담당업무
프론트앤드 개발
### 퇴사사유
경영 악화
### 프로젝트
- 골라라 트렌드 (구 MDLENS 트렌드) (2021.08  ~ 2022.07)
    - **What:** 소매가·도매 상품 검색 및 주문 가능한 커머스 사이트 개발  
    - **How:**  
      - Angular 7 → 13 마이그레이션  
      - Module Federation 도입하여 서비스 분리 및 확장성 확보  
      - 상품·매장·트렌드·마켓 리포트·스타일 정보 제공 기능 개발  
    - **Impact:**  
      - 대규모 서비스 구조 확장 가능  
      - 최신 Angular 환경으로 안정성과 성능 개선  
- 골라라 엉클(구 MDLENS 사입) (2021.08  ~ 2022.07)
    - **What:** 동대문 사입 삼촌 대상 사이트 유지보수  
    - **How:** Angular 7 → 13 마이그레이션 및 기능 안정화  
    - **Impact:** 서비스 안정성과 사용자 경험 향상  
- 골라라 파트너스(구 MDLENS 도매) (2021.08  ~ 2022.07)
    - **What:** 동대문 도매 대상 상품 등록 및 주문 관리 플랫폼  
    - **How:** Angular 7 → 13 마이그레이션 및 성능 최적화  
    - **Impact:** 주문 관리 안정성 확보 및 사용자 편의성 향상  
## 와이즈패션 (2020.03  ~ 2021.07)
### 담당업무
프론트앤드 개발
### 퇴사사유
서비스 합병
### 프로젝트
- MDLENS 트렌드 (2021.05  ~ 2021.07)
    - **What:** 동대문 패션 분석 및 정보 제공 사이트 개발  
    - **How:** Angular 7 기반 상품·매장·트렌드·마켓 리포트·스타일 기능 구현  
    - **Impact:** 동대문 패션 시장 내 정보 접근성 강화  
- MDLENS 사입 & MDLENS 도매 (2020.03  ~ 2021.07)
    - **What:** 동대문 사입 및 도매 플랫폼 유지보수 및 기능 개선  
    - **How:** 기능 모듈화, 코드 재사용성 향상(MD톡톡 등)  
    - **Impact:** 유지보수 효율 및 코드 품질 향상  
## 지볼티코리아 (2016.11 ~ 2020.02)
### 담당업무
연구개발, 원시 데이터를 이용하여 웹으로 시각화하는 부분을 담당.
### 퇴사사유
경영악화
### 프로젝트
- ZESTER WEB (2016.11~2020.02)
    - **What:** 무선 통신 원시 데이터 기반 시각화 Web App 개발  
    - **How:**  
      - MongoDB 데이터 모델링  
      - D3.js, Crossfilter.js 활용 시각화 라이브러리 직접 구현  
      - Node.js 백엔드 → Java/Kotlin Spring 마이그레이션  
    - **Impact:** 데이터 처리 속도 및 안정성 확보, 시각화 도구 고도화
- FieldBox (2018.01~2020.02)
    - **What:** 무선 필드 테스트 플랫폼(Web + Android) 개발  
    - **How:**
        - Web 및 Android 앱 프론트엔드 개발
        - MQTT 기반 실시간 데이터 전송 및 시각화 구현
        - 실시간 데이터 시각화 UI 개발
    - **Impact:**
        - 실제 필드에서 테스트할 수 있는 시스템 구축
        - 실시간 테스트 데이터 활용 가능, 분석 효율 개선  
## k4m (2016.01 ~ 2016.07)
### 담당업무
si, sm
### 퇴사사유
연구개발 배치 약속 불이행으로 퇴사 
### 프로젝트
- 정부3.0 정보공개 유지보수 (2016.01~2016.07)
    - **What:** 정부3.0 정보공개 사이트 안정적 운영  
    - **How:** Java, Oracle 기반 유지보수 및 API 개발  
    - **Impact:** 정보공개 API 성공적 배포 및 안정적 운영  
- 정부3.0 박람회 정보공개 체험 프로젝트 (2016.04~2016.05)
    - **What:** 박람회용 HTML 체험형 서비스 개발  
    - **How:** D3.js 기반 인터랙티브 시각화 및 터치 UI 구현  
    - **Impact:** 전시 현장에서 체험형 서비스로 호평  
## 이노아이씨티 (2014.10 ~ 2015.12)
### 담당업무
시각화 프로그램 설계 및 개발
### 퇴사사유
기업 흡수합병
### 프로젝트
- i3ware (2014.10~2015.12)
    - **What:** AngularJS + D3.js 기반 시각화 소프트웨어 개발  
    - **How:**
        - MEAN 스택 기반 아키텍쳐 설계 및 개발
        - Crossfilter.js 활용, UI 설계 및 개발
    - **Impact:** 데이터 분석 및 시각화 SW 개발  
## 미네르바 소프트 (2013.04 ~ 2014.05)
### 담당업무
MagicCloud 개발 담당, 보안USB DB 담당
### 퇴사사유
개인사정
### 프로젝트
- Magic Cloud (2013.10~2014.03)
    - **What:** 문서중앙화 Web App 개발  
    - **How:** PHP, jQuery 기반 사용자 관리·게시판·공유 그룹 기능 개발  
    - **Impact:** 사내 문서 공유 및 관리 효율성 증대  
- 보안 USB (2013.10~2014.03)
    - **What:** 보안 USB 웹 페이지 및 DB 관리  
    - **How:** Java, MS-SQL 기반 시스템 유지보수  
    - **Impact:** 안정적 서비스 운영 지원  

# 기타 프로젝트
## 팀 골라라 프론트 (2022.07  ~ 2022.08)
프론트 팀의 환상적인 팀웍으로 골라라에서 마지막 한달동안 작업한 **콘핑**이 세상에 나오지도 못한게 아까워 Backend 와 Flutter App 을 걷어내고 서버리스로 프로젝트를 진행
### 프로젝트
- 콘핑 (2022.07  ~ 2022.08)
    - 개요
        - 골라라tv 콘텐츠와 네이버 쇼핑 상품 연동 콘텐츠 커머스 플랫폼 개발 프로젝트 (상품 제외 기능 구현)
    - 성과
        - Backend 및 Flutter 앱 제거 후 서버리스 아키텍처로 전환하여 개발 진행
        - BFF(Backend For Frontend) 구현 및 Backend 연결 해제 후 Google API 기반 자동 데이터 연동 구축
        - Android WebView를 활용한 콘핑 앱 개발
        - 웹과 앱 간 인터페이스 및 딥링크(공유) 기능 구현
    - 상세 역할
        - BFF 구현 및 Google API [골라라tv](https://www.youtube.com/channel/UCQU44DD_X3LwgHjTPvs9LvQ) 연동 담당
        - Android WebView 앱 개발 및 딥링크 기능 개발
        - Firestore 데이터 자동 업데이트 로직 구현
    - 참여기술
        - SvelteKit, TypeScript, GraphQL, Google APIs, Firestore, GCP
    - 링크
        - [콘핑 웹(모바일)](https://conping-yqoln5urha-an.a.run.app)
        - [콘핑 앱 (구글 플레이)](https://play.google.com/store/apps/details?id=com.dj.conping) (현재 앱은 계정 문제로 내려감)
## 휴식2 (2016.08 ~ 2016.10)
### 담당업무
자기개발을 위한 휴식기
### 프로젝트
- DJ Cloud for Node (2016.08~2016.09)
    - 개요: MEAN 스택을 이용하여 웹하드 구현
    - 참여기술: MongoDB, Express, AngularJS, Node, jquery
    - 주요기능 :
        - 반응형 웹, 멀티 파일 및 폴더 다운로드, 미디어 플레이어 및 미디어 뷰어
        - https://www.youtube.com/watch?v=xy73_Ov6BOk
## 휴식1 (2014.06 ~ 2014.09)
### 담당업무
회사 업무에 신경쓰지 않고 Java를 다뤄보고 싶어서 자기개발을 위한 휴식기
### 프로젝트
- DJ Cloud for Java (2014.06~2014.08)
  - 개요: Java 공부를 하기위해 Java 와 jquery를 이용한 웹하드 구현
  - 참여기술: Java, Mybatis, Servlet, JSTL, jquery, MariaDB
  - 주요기능 :
    - 언어 선택, 미디어 뷰어 (이미지/동영상), 드래그/멀티/폴더 업로드, ContextMenu, 모바일 웹
    - https://firebasestorage.googleapis.com/v0/b/conpingstore.appspot.com/o/djcloud.pdf?alt=media&token=3954213c-e7b4-4dec-a350-1ae61a7b164c


# 기술
- Java
- Android
- Javascript
- Typescript
- AngularJS
- Angular
- Svelte
- SvelteKit
- Next.js
- React
- nestJS
- D3.js
- Crossfilter.js
- Socket.io
- Webpack
- Module Federation
- MongoDB
- Oracle
- Mysql
- Mssql
- graphql
