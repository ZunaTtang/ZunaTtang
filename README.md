<!-- ZunaTtang / 주나 — Profile README -->

# 👋 안녕하세요, 주나(Zuna)입니다

### AI 자동화 빌더 · Product / Growth Ops Engineer

저는 **Claude를 비롯한 AI를 실제 업무 시스템에 녹여 넣는 일**을 합니다.
복잡하고 반복적인 운영 업무를, 측정 가능하고 재사용 가능한 자동화 시스템으로 바꾸는 데 집중합니다.

제 작업은 **프로덕트 · 그로스 · 운영 · 엔지니어링**의 경계에 있습니다.
비즈니스 팀이 "지금 당장" 동작하는 도구가 필요할 때, 정식 개발 사이클보다 빠르게 만들어 검증하고 개선합니다.

> **반복되는 운영 통증 발견 → 작은 시스템 설계 → 빠른 출시 → 실사용으로 검증 → 신호 기반 개선**

---

## 🤖 Claude로 무엇을 했나 (핵심 포인트)

단순히 "AI를 써봤다"가 아니라, **Claude를 프로덕션 워크플로우의 의사결정 엔진과 운영 자동화의 핵심 부품으로** 사용했습니다.

| 활용 방식 | 어디에 썼나 | 만들어낸 가치 |
|---|---|---|
| **Claude Code Judge** | QA 회귀 탐지 파이프라인에서 의심 케이스만 Claude 세션으로 보내 최종 판정 | 자동화의 고질적 문제인 **노이즈/오탐을 사람 대신 걸러냄** |
| **Claude Code Routines** | 매일 정해진 시간에 Intercom 대화를 요약해 Slack에 발행 | **서버리스 인프라 없이** AI 운영 루틴 상시 가동 (AWS Lambda → Routine 이관) |
| **Claude API** | 크립토 시장 데이터를 전문가 수준 브리핑으로 변환 | 데이터 수집 + AI 해석 + 자동 배포를 하나의 **콘텐츠 운영 파이프라인**으로 |
| **MCP (Model Context Protocol)** | Intercom · Slack 등 외부 도구를 AI에 직접 연결 | 코드 글루 없이 **AI가 실제 업무 시스템을 조작** |

**핵심 차별점:** 저는 AI를 "답변기"가 아니라 **사람의 판단이 필요한 지점을 아는 운영 시스템의 일부**로 설계합니다.
언제 자동화하고, 언제 멈춰 사람에게 물어야 하는지를 시스템 안에 녹입니다.

---

## 🚀 주요 프로젝트

### 1. ClientBrief — 비개발자용 주간 개발 리포트 SaaS
> GitHub PR · Issue · Review · Comment 데이터를 **비개발자도 읽기 쉬운 주간 리포트**로 자동 생성하고, 검토 → 승인 → 이메일 발송까지 처리하는 SaaS.

- **스택:** Next.js 14 (App Router) · React 18 · TypeScript 5 · PostgreSQL · Prisma 5 · NextAuth.js · Tailwind · Zod
- **핵심 기능:** GitHub OAuth 연동 데이터 수집 · 민감정보 자동 마스킹(`[REDACTED]`) · AI 7섹션 리포트 생성 · `draft → approved → sent` 승인 워크플로우 · Resend 이메일 발송 · 멀티 테넌트 구조
- **왜 의미 있나:** "이번 주 뭐 했는지"를 매주 손으로 정리하던 시간을 제거. **풀스택 SaaS를 혼자 설계·구현**한 결과물.

🔗 [`clientbrief`](https://github.com/ZunaTtang/clientbrief)

### 2. Web QA 자동화 도구 — Claude Code Judge 회귀 탐지 파이프라인
> Playwright + TypeScript 기반 재사용 QA 도구. 범용 헬스체크부터 **빌드 간 회귀를 자동 탐지하고 Claude로 노이즈를 걸러내는** 파이프라인까지.

- **스택:** Playwright · TypeScript · Claude Code (Judge) · TUI 메뉴 런처
- **2계층 구조:** ① 범용 QA(smoke/regression/crawler/visual/a11y) — `QA_BASE_URL`만 바꾸면 어떤 사이트든 적용 ② 회귀 탐지 — 페이지를 구조적으로 스냅샷(접근성 트리·API 스키마·콘솔/네트워크·픽셀)하고 baseline과 비교, **의심 케이스만 Claude 판정**, CI에 종료 코드(0/1/2) 반환
- **왜 의미 있나:** 수동 QA를 **반복 가능한 운영 품질 게이트**로 전환. AI를 회귀 탐지의 판단 레이어로 통합.

🔗 `qa-automation` *(비공개 / 데모 요청 가능)*

### 3. Intercom Daily Digest Routine — AI CS 운영 루틴
> 매일 오전 Intercom의 열린 대화를 요약·분류해 Slack에 발행하는 Claude Code Routine.

- **스택:** Claude Code Routines (Anthropic 관리형) · Intercom MCP · Slack MCP · Sonnet 4.6
- **핵심:** 미할당/봇 대화 필터링 → 우선순위 분류(🔴긴급/🟠조치필요/🟡대기/🟢모니터) → Slack Block Kit 메시지
- **엔지니어링 판단:** AWS Lambda + EventBridge에서 Routine으로 이관 → **운영 부담↓, 보안↑**(루트 크리덴셜·수동 배포 제거)

🔗 [`intercom-digest-routine`](https://github.com/ZunaTtang/intercom-digest-routine)

### 4. Crypto Market Briefing Bot — AI 시장 브리핑 자동화
> 여러 시장 데이터 소스를 모아 Claude API로 전문가 수준 브리핑을 만들고 Telegram으로 매일 발송하는 봇.

- **스택:** Python · Telegram Bot API · Claude API · GCP Cloud Scheduler · Docker
- **수집 신호:** ETF 플로우 · 미결제약정(OI) · 펀딩비 · 코인베이스 프리미엄 · 공포탐욕지수 · 알트시즌 지수
- **왜 의미 있나:** 재시도·에러 핸들링이 포함된 견고한 스크래퍼 + AI 해석 + 자동 배포의 **end-to-end 콘텐츠 파이프라인**.

🔗 [`briefing-bot`](https://github.com/ZunaTtang/briefing-bot)

### 5. Tap-to-Sync — 숏폼 자막 싱크 자동화 MVP
> 숏폼 편집자가 **Tap 기반 UX + 자동 보정 엔진**으로 자막 싱크 시간을 크게 줄이는 Web MVP.

- **스택:** React · TypeScript · Vite · Tailwind CSS
- **핵심:** 재생 중 Tap/단축키로 timestamp 등록 → monotonic 보장·minGap·smoothing·길이 기반 분배 보정 → SRT / LRC / CapCut CSV 3종 export
- **왜 의미 있나:** 수동 창작 워크플로우를 **집중된 생산성 도구**로 전환한 제품 사고의 예시.

🔗 [`taptosync`](https://github.com/ZunaTtang/taptosync)

### 6. Web Screenshot Autobot — 로그인 지원 웹 크롤러
> Python + Playwright 기반 CLI 크롤러. 내부 링크를 BFS로 탐색하며 전체화면 스크린샷을 자동 저장(로그인 세션 지원).

🔗 [`auto-screenshot-bot`](https://github.com/ZunaTtang/auto-screenshot-bot)

---

## 🧰 핵심 역량

**AI & 자동화**
`Claude Code (Judge/Routines)` · `Claude API` · `OpenAI API` · `MCP` · `프롬프트 기반 프로세스 자동화` · `Human-in-the-loop 설계`

**프로덕트 & 그로스 옵스**
`캠페인 운영` · `유저 행동 분석` · `CRM/CS 워크플로우` · `퍼널 모니터링` · `그로스 실험 운영` · `커뮤니티 자동화`

**기술 스택**
`TypeScript` · `Python` · `React / Next.js` · `Node.js` · `PostgreSQL / Prisma` · `Playwright` · `Docker` · `GCP` · `REST / Webhook` · `Slack / Telegram / Intercom 연동`

**데이터 & 신호**
`Amplitude` · `운영 메트릭` · `QA 신호 설계` · `시장 데이터 모니터링` · `리포팅 파이프라인`

---

## 💭 일하는 방식

좋은 자동화 시스템은 코드 그 이상입니다. 다음을 알아야 합니다.

- **누가** 쓰는가
- **어떤 의사결정**을 돕는가
- **실패**는 어떤 모습인가
- 사람은 결과를 **어떻게 검토**하는가
- 자동화가 **언제 멈추고** 판단을 요청해야 하는가

그래서 저는 **운영을 이해하는 개발(operation-aware development)** 을 지향합니다 — 실제 팀 워크플로우 안에서 동작하는 작은 시스템을 만드는 것.

> **한 줄 요약:** 저는 프로덕트·그로스 팀이 수동 병목 없이 더 빠르게 움직이도록, AI 기반 운영 시스템을 만듭니다.

---

## 📫 연락처

- GitHub: [@ZunaTtang](https://github.com/ZunaTtang)

---
---

# 👋 Hi, I'm Zuna

### AI Automation Builder · Product / Growth Ops Engineer

I build **real operational systems with AI — Claude in particular — at their core.**
My focus is turning messy, repetitive operations into measurable, reusable automation.

My work sits at the intersection of **product, growth, operations, and engineering** — the space where business teams need a *working* tool faster than a normal product cycle can deliver.

> **Find repetitive operational pain → design a small system → ship fast → validate with real usage → improve from signals.**

---

## 🤖 What I've Built With Claude (the core story)

Not "I tried an AI" — I use **Claude as the decision engine in production workflows and the core component of operational automation.**

| How I used it | Where | Value created |
|---|---|---|
| **Claude Code Judge** | QA regression pipeline routes only suspicious cases to a Claude session for the final verdict | Solves automation's classic problem — **filtering noise/false positives without a human** |
| **Claude Code Routines** | Summarizes Intercom conversations and posts to Slack on a daily schedule | Always-on AI ops **with zero serverless infra** (migrated off AWS Lambda) |
| **Claude API** | Turns crypto market data into expert-level briefings | Data ingest + AI interpretation + auto-delivery as **one content pipeline** |
| **MCP (Model Context Protocol)** | Connects Intercom, Slack, etc. directly to the AI | The **AI operates real business systems** without glue code |

**The differentiator:** I design AI not as an "answer box" but as **part of an operational system that knows where human judgment is needed** — when to automate, and when to stop and ask.

---

## 🚀 Featured Projects

### 1. ClientBrief — Weekly Dev Report SaaS for Non-Engineers
> Auto-generates **non-engineer-friendly weekly reports** from GitHub PR · Issue · Review · Comment data, with a review → approve → email-send flow.

- **Stack:** Next.js 14 (App Router) · React 18 · TypeScript 5 · PostgreSQL · Prisma 5 · NextAuth.js · Tailwind · Zod
- **Highlights:** GitHub OAuth ingestion · automatic secret masking (`[REDACTED]`) · AI 7-section report generation · `draft → approved → sent` state machine · Resend email delivery · multi-tenant org model
- **Why it matters:** Removes the weekly manual "what did we ship?" write-up. A **full-stack SaaS designed and built solo.**

🔗 [`clientbrief`](https://github.com/ZunaTtang/clientbrief)

### 2. Web QA Automation Tool — Claude Code Judge Regression Pipeline
> A reusable Playwright + TypeScript QA toolkit, from generic health checks to a pipeline that **auto-detects cross-build regressions and filters noise with Claude.**

- **Stack:** Playwright · TypeScript · Claude Code (Judge) · TUI launcher
- **Two layers:** ① Generic QA (smoke/regression/crawler/visual/a11y) — point `QA_BASE_URL` at any site ② Regression detection — structurally snapshots each page (a11y tree · API schema · console/network · pixels) vs. baseline, **routes only suspect cases to Claude**, returns CI exit codes (0/1/2)
- **Why it matters:** Turns manual QA into a **repeatable operational quality gate** with AI as the judgment layer.

🔗 `qa-automation` *(private — demo available on request)*

### 3. Intercom Daily Digest Routine — AI CS Ops Routine
> A Claude Code Routine that summarizes and triages open Intercom conversations into Slack every morning.

- **Stack:** Claude Code Routines (Anthropic-managed) · Intercom MCP · Slack MCP · Sonnet 4.6
- **Core:** filters unassigned/bot chats → priority triage (🔴urgent/🟠action/🟡pending/🟢monitor) → Slack Block Kit message
- **Engineering call:** migrated from AWS Lambda + EventBridge to Routines → **lower ops overhead, better security** (no root creds, no manual deploy)

🔗 [`intercom-digest-routine`](https://github.com/ZunaTtang/intercom-digest-routine)

### 4. Crypto Market Briefing Bot — AI Market Briefings
> Collects multiple market data sources, generates expert-level briefings via the Claude API, and delivers them daily over Telegram.

- **Stack:** Python · Telegram Bot API · Claude API · GCP Cloud Scheduler · Docker
- **Signals:** ETF flows · open interest · funding rates · Coinbase premium · Fear & Greed · Altcoin Season index
- **Why it matters:** A robust scraper (retries + error handling) + AI interpretation + auto-distribution as an **end-to-end content pipeline.**

🔗 [`briefing-bot`](https://github.com/ZunaTtang/briefing-bot)

### 5. Tap-to-Sync — Short-form Subtitle Sync MVP
> A web MVP that slashes subtitle-syncing time for short-form editors via a **tap-based UX + auto-correction engine.**

- **Stack:** React · TypeScript · Vite · Tailwind CSS
- **Core:** tap/hotkey timestamps during playback → monotonic guarantee, minGap, smoothing, length-based distribution → export to SRT / LRC / CapCut CSV
- **Why it matters:** Product thinking that converts a manual creative workflow into a focused productivity tool.

🔗 [`taptosync`](https://github.com/ZunaTtang/taptosync)

### 6. Web Screenshot Autobot — Login-aware Crawler
> A Python + Playwright CLI crawler that BFS-traverses internal links and auto-captures full-page screenshots (supports authenticated sessions).

🔗 [`auto-screenshot-bot`](https://github.com/ZunaTtang/auto-screenshot-bot)

---

## 🧰 Core Capabilities

**AI & Automation** — `Claude Code (Judge/Routines)` · `Claude API` · `OpenAI API` · `MCP` · `prompt-based process automation` · `human-in-the-loop design`

**Product & Growth Ops** — `campaign operations` · `user behavior analysis` · `CRM/CS workflows` · `funnel monitoring` · `growth experiments` · `community automation`

**Technical** — `TypeScript` · `Python` · `React / Next.js` · `Node.js` · `PostgreSQL / Prisma` · `Playwright` · `Docker` · `GCP` · `REST / Webhooks` · `Slack / Telegram / Intercom integrations`

**Data & Signals** — `Amplitude` · `operational metrics` · `QA signal design` · `market data monitoring` · `reporting pipelines`

---

## 💭 How I Think

A good automation system is more than code. It has to understand:

- **who** uses it
- what **decision** it supports
- what **failure** looks like
- how humans **review** the result
- when automation should **stop and ask** for judgment

That's why I aim for **operation-aware development** — small systems that work inside real team workflows.

> **One-liner:** I build AI-powered operational systems that help product and growth teams move faster with fewer manual bottlenecks.

---

## 📫 Contact

- GitHub: [@ZunaTtang](https://github.com/ZunaTtang)
