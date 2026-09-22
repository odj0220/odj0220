# 경력

## 피트릭스 (2026.02 ~ 현재)

### 담당업무

개발팀장, 백엔드 · 프론트엔드 · Unity · 키오스크 런처 · CI/CD 전반 개발 및 관리

### 프로젝트

* 스마트미러 측정 서비스 공통 아키텍처 및 개발 체계 (2026.02 ~ 현재)

  * **What:** 기존에 없던 공통 개발·배포 체계를 새롭게 구축하고, 여러 기술과 방식으로 파편화되어 있던 백엔드·웹·Unity 서비스를 하나의 기술 스택과 개발 체계로 통합
  * **How:**

    * 서버·Unity 클라이언트·리포트마다 개별적으로 관리되던 측정 항목 정의를 `com.outbody.spec` 단일 스펙 레포로 통합 — 19개 측정 항목의 키·DB 필드·등급 판정 기준을 SSOT로 정의하고 Unity(UPM)·서버(npm)가 동일 패키지를 참조하도록 구축
    * 구두·개별 문서로 관리되던 API 스펙을 레포 내 설계 문서로 체계화하고 리포트 v2·SW Edition·Fitness·grade-criteria·QR 로그인·Apple 로그인 등 12종 API 스펙 및 Swagger 표준화
    * 클라이언트마다 중복 구현되어 있던 등급 판정 로직을 서버 단일 소스로 통합하고 Unity 자체 판정 로직 제거 — 판정 기준 번들 API와 골든 벡터를 도입하여 클라이언트·서버 간 판정 결과 파리티 검증 체계 구축
    * jQuery 임베디드·Vue·Vite-React 등 서로 다른 기술로 구현되어 있던 4개 프론트 앱을 Next.js 15·React 19 단일 스택으로 통일하고 Turborepo 모노레포 및 공통 패키지(`@fx-fe/ui`·`utils`·`report-pdf`·`report-fitness`) 구축
    * 기존 레거시 구조와 중복 구현을 분석하여 불필요한 의존성·구현을 제거하고 공통 모듈로 통합 — 기술 부채를 해소하고 백엔드·프론트엔드·Unity 간 기술 스택 및 개발 방식 표준화
    * GitHub Actions 기반 CI/CD와 Azure Container Apps 자동 배포 체계를 신규 구축하고 태그 기반 상용 릴리즈 프로세스 정립
    * Claude API를 활용한 릴리즈 노트 자동 생성·GitHub Release 자동 발행, MS Teams 배포 알림·Notion 배포 이력 자동화 체계 신규 구축
    * Claude Code PR 자동 리뷰를 백엔드·프론트엔드·Unity 전 레포에 도입하여 기존에 없던 자동 코드 리뷰 1차 게이트 구축
    * Git 브랜치·배포 전략을 새롭게 정의하여 `PR 머지 = 상용 배포`, `development 직접 머지 = QA 배포`로 릴리즈 프로세스 표준화
  * **Impact:**

    * 기존에 없던 개발·배포·릴리즈·코드 리뷰 체계를 구축하여 팀의 개발 프로세스 표준화
    * 서로 다른 기술로 구현된 레거시 서비스를 Next.js 15·React 19 중심의 단일 기술 스택으로 통합하여 기술 부채 해소
    * 중복 구현·불필요한 의존성·분산된 기준을 정리하고 공통 모듈 및 SSOT 기반으로 구조 개선
    * 측정 항목·등급 판정 기준을 단일 소스로 통합하여 클라이언트와 서버 간 기준 불일치 문제 구조적 제거
    * 수동 배포·릴리즈 문서 작성·배포 이력 관리·코드 리뷰 등 반복적인 운영 업무 자동화
    * 백엔드·웹·Unity·키오스크 런처까지 동일한 개발·배포 체계로 확장 가능한 기반 구축

* Fittrix 스마트미러 측정 서비스 백엔드 (2026.02 ~ 현재)

  * **What:** 스마트미러 기반 체형·체성분·체력 측정 서비스의 멀티 테넌트 API 서버 개발 및 운영
  * **How:**

    * 체형·자세·스크리닝·골프·다이어트·kids/teens 등 도메인별 PDF 리포트 v2 API 신규 설계·런칭 (v2.4 → v2.9 단독 주도)
      + 4개 언어(한국어·영어·일본어·번체 중국어) 다국어 리포트 및 미지원 언어 자동 폴백 구현
    * Fitness 체력측정 저장·판정 시스템 신규 설계 — 17종 측정 항목, 연령대별 측정 그룹 카탈로그, 항목 → 섹션 → 영역 → 종합 등급 판정 체계 구축
    * `grade-criteria` 판정 기준 번들 API 설계 — 클라우드 단선 시에도 앱에서 서버와 동일한 기준으로 등급 재현 가능하도록 오프라인 판정 지원
    * 지역·레거시·구독 등급에 얽혀 있던 기능 분기를 `구독 여부 / sw_edition / service_mode` 3축의 SW Edition 체계로 재설계하고 미러 펌웨어 하위호환 및 백필 마이그레이션 수행
    * 키오스크 QR 로그인에서 Firebase 의존성을 제거하고 `shortKey` 세션 기반 인증으로 재구현 — QR 갱신 레이스 제거 및 다중 인스턴스 환경에서 토큰 단일 발급 보장
    * 카카오·구글·Apple 소셜 로그인 및 비밀번호 재설정·최초 설정 API 구현, 소셜 로그인 공통 모듈화 및 기존 phone-only 계정 무중단 연동
    * Admin 로그인 Microsoft Entra ID(OIDC) 전환 및 Admin 구독 관리 시스템 구축, Stripe 결제 연동
    * 자세 측정 등급 경계값을 `round → floor` 방식으로 일관화하고 심각도 기반 worst-item 및 예측모델 rank 기준 재정의
    * 회원 생성 레이스 컨디션에 의한 중복 계정을 MySQL Named Lock으로 방지하고 디바이스 토큰 인증 취약점 수정
    * 테스트 체계가 없던 레포에 단위 테스트 96건 + E2E 테스트 581건 구축, 운영 DB 오접속 가드 및 Firebase lazy init을 적용하여 E2E 하네스 안정화
    * 미사용 BullMQ·Redis·MongoDB·Firebase 코드 제거, RabbitMQ 재연결 무한 루프 수정, Region Mirror → Center 데이터 모델 정리, 파일 백업을 Azure Blob 직통 스트림 업로드로 전환
  * **Impact:**

    * 리포트 v2 런칭 및 Fitness 신규 사업 라인의 백엔드 기반 구축
    * SW Edition 상품화 및 구독 기반 서비스 확장을 위한 백엔드 구조 확보
    * 일본·대만 해외 서비스 확장 기반 확보 및 다국어 표시 장애 0건화
    * App Store 반려 이슈 해소 및 카메라 없는 매장·오프라인 환경까지 서비스 적용 범위 확대
    * 테스트 자동화 및 기술 부채 정리를 통해 서비스 안정성과 유지보수성 향상

* Fittrix Admin — 운영 관리자 콘솔 (2026.02 ~ 현재)

  * **What:** 백엔드에 jQuery로 임베디드되어 있던 레거시 관리자 화면을 독립 프론트엔드 서비스로 분리·재구축
  * **How:**

    * Next.js 15 App Router · React 19 기반 독립 콘솔 구축
    * 인증·사이드바 레이아웃·API 클라이언트 구조 설계 및 Microsoft Entra ID(Teams 조직 계정) OIDC 로그인 전환
    * 테마/모드/버전, 그룹·미러·관리자 계정, QnA·문의, CDN 관리, 키오스크 공지사항 기능 단독 구현
    * 구독·결제내역 관리 화면 구축 — 플랜·미러별 집계 및 수기/정기 결제 판단 기능 구현
  * **Impact:**

    * 백엔드 임베디드 jQuery 구조를 독립 서비스로 분리하여 유지보수성과 확장성 확보
    * B2B 구독·결제 운영 기능을 독립 콘솔로 일원화
  * **Legacy → Now:** jQuery (백엔드 임베디드) → Next.js 15 · React 19 · TypeScript · Radix UI · Tailwind CSS · i18next

* Fittrix Studio — 센터 운영 대시보드 (2026.02 ~ 현재)

  * **What:** 피트니스 센터 운영자를 위한 회원·검사·결제 관리 대시보드를 Next.js 기반으로 현대화하고 Fitness 기능 확장
  * **How:**

    * React 19 + Vite + React Router DOM 기반 앱을 Next.js 15 App Router로 이관하고 SSR 환경의 하이드레이션 오류 구조적 해소
    * Stripe·TossPayments SDK 연동 및 구독 상태 기반 접근 통제 일원화
    * WELLNESS/FITNESS 모드 분리 및 Fitness 대시보드·리포트 상세·AI 리포트 화면 신규 구축
    * Recharts 및 커스텀 차트 시각화 구현, 결측월 라인 끊김·라벨 클리핑 문제 해결
    * InBody·MBTI Unity WebGL을 `postMessage` 브릿지로 연동
    * TanStack Query optimistic update 적용 및 `queryClient` 싱글톤화로 캐싱 버그 제거
  * **Impact:**

    * 레거시 React/Vite 구조를 Next.js 기반으로 현대화하여 유지보수성 향상
    * 결제 플로우 통합 및 구독 상태 관리로 B2B 과금 체계 정립
    * Fitness 신규 사업 영역을 센터 운영 대시보드까지 확장
  * **Legacy → Now:** React 19 + Vite + React Router DOM → Next.js 15 · TanStack Query · Stripe · TossPayments · Recharts · Radix UI · dnd-kit · Unity WebGL · Tailwind CSS

* Fittrix Report — 측정 리포트 뷰어 (2026.02 ~ 현재)

  * **What:** Vue 기반 레거시 리포트 서비스를 Next.js로 전환하고 리포트 v2를 전면 재설계
  * **How:**

    * Vue SFC 26개 + vue-i18n + @coreui/vue-chartjs 구성을 Next.js 15 · React 19 · react-i18next · react-chartjs-2로 전면 이관, 27개 TSX 변환
    * 체형·자세·스크리닝·골프·다이어트·kids/teens 등 도메인별 리포트 v2 화면 신규 설계·런칭 (v2.4 → v2.5 단독 주도)
    * Fitness PDF 리포트 신규 구축 및 `@fx-fe/report-fitness` 패키지로 Studio·App 공용화
    * Chart.js 레이더 차트를 커스텀 SVG 차트로 대체하고 골프 스윙 탄도 등 도메인 특화 시각화 구현
    * A4 PDF 출력 대응 및 iOS Safari 스케일링 문제 해결로 화면과 인쇄 결과의 일관성 확보
      + 4개 언어 리포트 지원, `x-language` 헤더 전파 및 미지원 locale 자동 폴백 구현
    * PDF 로직을 `@fx-fe/report-pdf` 공유 패키지로 추출하여 사용자 앱과 공용화
  * **Impact:**

    * 리포트 v2 사용자 접점을 완성하여 신규 매출 채널 기반 마련
    * 일본·대만 서비스 확장에 대응하는 다국어 리포트 기반 확보
    * 웹 화면·PDF·모바일 환경 간 리포트 출력 일관성 확보
  * **Legacy → Now:** Vue + vue-i18n + @coreui/vue-chartjs → Next.js 15 · React 19 · 커스텀 SVG 차트 · react-chartjs-2 · react-i18next · Tailwind CSS

* Fittrix App — 사용자 클라이언트 (웹 + iOS/Android) (2026.02 ~ 현재)

  * **What:** React + Vite 기반 사용자 앱을 Next.js로 이관하고 소셜 로그인·QR 로그인·Fitness·AI 리포트 사용자 흐름 구축
  * **How:**

    * React 19 + Vite + React Router DOM 7 기반 앱을 Next.js 15 App Router로 이관
    * Unity WebView 래퍼인 FX-webview를 이용하여 iOS/Android 스토어 앱 구축 — JS 브릿지 규약, QR 딥링크(App Links/Universal Links), 쿠키 세션 유지, 스플래시·아이콘 대응
    * 카카오·구글·Apple OAuth 소셜 로그인 및 비밀번호 재설정·최초 설정 구현, 컨테이너 내부 `redirect_uri` 문제 해결
    * 키오스크 QR 로그인, FITNESS 탭·측정 결과·AI 리포트 화면 신규 구현
    * 마이페이지·프로필 수정·약관 동의 개편 및 회원가입 국가 자동 감지, 카카오 이름·gender fallback 적용
    * DOMPurify 적용, 쿠키 Secure 플래그 정리, Suspense 경계 처리로 prerender 빌드 오류 해결
  * **Impact:**

    * 웹과 네이티브 앱을 동일한 사용자 서비스 구조로 통합
    * 소셜·QR 로그인 도입으로 사용자 접근성과 편의성 향상
    * App Store 심사 대응 및 가입 실패 요인 개선
  * **Legacy → Now:** React 19 + Vite + React Router DOM 7 → Next.js 15 · OAuth(Kakao/Google/Apple) · Chart.js · QR Scanner · i18next · Tailwind CSS

* Unity 키오스크 클라이언트 — Wellness 미러 · Fitness · 국민체력100 (C#) (2026.02 ~ 현재)

  * **What:** 스마트미러 및 국민체력100 키오스크 3종의 공통 클라이언트 구조와 외부 측정기기 연동 개발
  * **How:**

    * 국민체력100 키오스크용 외부 의료기기 통합 매니저 설계·구현 — 체성분(BC380s)·혈압(BP600)·악력(KL-114)·좌전굴(KL-115)·제자리멀리뛰기(KL-M100)·반복달리기(K-100)·UWB·벽패스 등 8종 USB Serial/TCP 드라이버 및 프로토콜 파서 구현
    * VID/PID·Serial Number 기반 포트 자동 매핑, Mono SerialPort 세마포 충돌 회피를 위한 TX 워커 스레드 적용
    * 운영 빌드용 진단 HUD를 구현하여 현장 장비 세팅 및 장애 진단 부담 감소
    * 백엔드 API 매니저·QR 로그인 매니저·사용자 세션 공통 모듈 구현 및 3개 앱에서 재사용
    * Fitness 앱의 등급 판정 로직을 전면 제거하고 서버 단일 소스로 전환 — 판정 기준 번들 해석기·집계기 + ETag 캐시 + 오프라인 폴백으로 네트워크 단절 상황에서도 측정 가능하도록 구현
    * 런처 연동 프로토콜(APP_READY 핸드셰이크·부팅 진행률·앱 스위칭·세션 보관)을 미러/Fitness 양쪽에 구현하여 앱 전환 시 로그인 상태 유지
    * 미러 앱의 Destroy 누락 텍스처·머티리얼 회수, 세션 경계 이미지 캐시 정리, GC 비동기화 등을 통해 메모리 누수 수정
    * 리포트 로컬 프린터 인쇄 기능 구현 — 단기 인쇄 토큰 발급, Edge Headless PDF 생성, SumatraPDF 인쇄 상태 머신 구축
  * **Impact:**
    + 8종 외부 측정기기를 단일 통합 구조로 연결하여 국민체력100 키오스크의 하드웨어 확장 기반 확보

    * 서버 기준 기반의 등급 판정 및 오프라인 폴백으로 측정 신뢰성 향상
    * Unity 3개 앱에서 공통 인증·세션·API 모듈을 재사용할 수 있는 구조 확보
    * 현장 장비 설치·장애 대응 및 키오스크 운영 편의성 개선

* Fittrix Launcher — 키오스크 런처 (Electron + Vue) (2026.02 ~ 현재)

  * **What:** Wellness/Fitness 키오스크 앱의 설치·실행·업데이트·스위칭을 담당하는 런처 개발
  * **How:**

    * 미러/Fitness 앱 다운로드·설치·실행·스위칭 프로세스 설계 및 구현
    * TCP 프로토콜 서버 구현 — APP_READY 핸드셰이크 기반 스플래시 reveal, 부팅 진행률 표시, 로케일 전환 및 로그인 세션 보관
    * Azure Storage 환경별 동적 전환 및 CDN 경유 다운로드 구현, 실패 시 Storage 자동 폴백
    * locale별 다운로드 캐시를 적용하여 불필요한 재다운로드 방지
    * 버전 판정을 일원화하여 재설치 누락 및 구버전 실행 문제 해결
    * GitHub Actions 기반 런처 배포 워크플로우 구축
  * **Impact:**

    * 키오스크 앱 설치·업데이트·실행 과정을 자동화하여 현장 운영 부담 감소
    * 미러/Fitness 앱 간 안정적인 전환 및 세션 유지
    * CDN 장애 상황에서도 Storage 폴백을 통한 배포 안정성 확보

## 와그 (2022.09  ~ 2025.05)

### 담당업무

프론트앤드 개발, 웹 팀장

### 프로젝트

* 와그 모던 개발 (2022.09  ~ 2023.06)

  * **What:** 기존 레거시 와그웹을 대체하는 신규 플랫폼 개발
  * **How:**

    * 모노레포 아키텍처 설계 및 도입
    * Next.js + NestJS 기반 프론트/백엔드 개발 총괄
    * BFF(Backend For Frontend) 아키텍처 적용
    * AWS, Jenkins, CodeDeploy 기반 CI/CD 구축
    * GTM 도입 및 마케팅 스크립트 코드 분리
    * STG 서버 구축 및 Winston 기반 로그 체계 마련
  * **Impact:**

    * 웹 성능 지표 및 검색 노출 향상 → 신규 유저 유입 증가
    * 배포 자동화로 개발 생산성 및 운영 안정성 확보
    * 모던 아키텍처 도입으로 장기적 유지보수성·확장성 개선

* 와그 웹 신규기능 추가 및 유지보수 (MAU 100만)

  * **What:** 기존 레거시 사이트를 모던 스택으로 이관하고, 신규 기능을 지속적으로 개발/운영
  * **How:**

    * Next.js Pages Router → App Router 전환 및 마이그레이션 (Next.js 12 → 14 → 15)
    * React 19 업그레이드 및 마이그레이션 수행 (Next.js 14 → 15 전환시 진행)
    * Nginx 기반 무중단 배포 파이프라인 설계 및 운영
    * ELK 스택 도입으로 로그 및 마케팅 데이터 수집 체계 구축
    * 데이터 분석을 위한 대시보드 및 시각화 기능 개발
  * **Impact:**

    * 모바일 웹 바이탈 점수 90% "나쁨" → 95% "좋음"으로 개선
    * 무중단 배포로 배포 안정성 확보 및 장애 최소화
    * 마케팅 데이터 기반 의사결정 프로세스 고도화

## 골라라 (2021.08  ~ 2022.07)

### 담당업무

프론트앤드 개발

### 퇴사사유

경영 악화

### 프로젝트

* 골라라 트렌드 (구 MDLENS 트렌드) (2021.08  ~ 2022.07)

  * **What:** 소매가·도매 상품 검색 및 주문 가능한 커머스 사이트 개발
  * **How:**

    * Angular 7 → 13 마이그레이션
    * Module Federation 도입하여 서비스 분리 및 확장성 확보
    * 상품·매장·트렌드·마켓 리포트·스타일 정보 제공 기능 개발
  * **Impact:**

    * 대규모 서비스 구조 확장 가능
    * 최신 Angular 환경으로 안정성과 성능 개선

* 골라라 엉클(구 MDLENS 사입) (2021.08  ~ 2022.07)

  * **What:** 동대문 사입 삼촌 대상 사이트 유지보수
  * **How:** Angular 7 → 13 마이그레이션 및 기능 안정화
  * **Impact:** 서비스 안정성과 사용자 경험 향상

* 골라라 파트너스(구 MDLENS 도매) (2021.08  ~ 2022.07)

  * **What:** 동대문 도매 대상 상품 등록 및 주문 관리 플랫폼
  * **How:** Angular 7 → 13 마이그레이션 및 성능 최적화
  * **Impact:** 주문 관리 안정성 확보 및 사용자 편의성 향상

## 와이즈패션 (2020.03  ~ 2021.07)

### 담당업무

프론트앤드 개발

### 퇴사사유

서비스 합병

### 프로젝트

* MDLENS 트렌드 (2021.05  ~ 2021.07)

  * **What:** 동대문 패션 분석 및 정보 제공 사이트 개발
  * **How:** Angular 7 기반 상품·매장·트렌드·마켓 리포트·스타일 기능 구현
  * **Impact:** 동대문 패션 시장 내 정보 접근성 강화

* MDLENS 사입 & MDLENS 도매 (2020.03  ~ 2021.07)

  * **What:** 동대문 사입 및 도매 플랫폼 유지보수 및 기능 개선
  * **How:** 기능 모듈화, 코드 재사용성 향상(MD톡톡 등)
  * **Impact:** 유지보수 효율 및 코드 품질 향상

## 지볼티코리아 (2016.11 ~ 2020.02)

### 담당업무

연구개발, 원시 데이터를 이용하여 웹으로 시각화하는 부분을 담당.

### 퇴사사유

경영악화

### 프로젝트

* ZESTER WEB (2016.11~2020.02)

  * **What:** 무선 통신 원시 데이터 기반 시각화 Web App 개발
  * **How:**

    * MongoDB 데이터 모델링
    * D3.js, Crossfilter.js 활용 시각화 라이브러리 직접 구현
    * Node.js 백엔드 → Java/Kotlin Spring 마이그레이션
  * **Impact:** 데이터 처리 속도 및 안정성 확보, 시각화 도구 고도화

* FieldBox (2018.01~2020.02)

  * **What:** 무선 필드 테스트 플랫폼(Web + Android) 개발
  * **How:**

    * Web 및 Android 앱 프론트엔드 개발
    * MQTT 기반 실시간 데이터 전송 및 시각화 구현
    * 실시간 데이터 시각화 UI 개발
  * **Impact:**

    * 실제 필드에서 테스트할 수 있는 시스템 구축
    * 실시간 테스트 데이터 활용 가능, 분석 효율 개선

## k4m (2016.01 ~ 2016.07)

### 담당업무

si, sm

### 퇴사사유

연구개발 배치 약속 불이행으로 퇴사

### 프로젝트

* 정부3.0 정보공개 유지보수 (2016.01~2016.07)

  * **What:** 정부3.0 정보공개 사이트 안정적 운영
  * **How:** Java, Oracle 기반 유지보수 및 API 개발
  * **Impact:** 정보공개 API 성공적 배포 및 안정적 운영

* 정부3.0 박람회 정보공개 체험 프로젝트 (2016.04~2016.05)

  * **What:** 박람회용 HTML 체험형 서비스 개발
  * **How:** D3.js 기반 인터랙티브 시각화 및 터치 UI 구현
  * **Impact:** 전시 현장에서 체험형 서비스로 호평

## 이노아이씨티 (2014.10 ~ 2015.12)

### 담당업무

시각화 프로그램 설계 및 개발

### 퇴사사유

기업 흡수합병

### 프로젝트

* i3ware (2014.10~2015.12)

  * **What:** A
