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
| **AI 비용 엔지니어링** | 운명재판소 게임 — 캐시·프리셋·룰베이스 폴백 **다계층 라우팅**으로 AI 호출 단가를 0원에 근접 | *"판당 흑자"*가 유지되는 **AI 경제 구조**를 직접 설계 (provider 추상화로 모델 스왑) |
| **Claude API** | 크립토 시장 데이터를 전문가 수준 브리핑으로 변환 | 데이터 수집 + AI 해석 + 자동 배포를 하나의 **콘텐츠 운영 파이프라인**으로 |
| **Notion MCP** | 기존에 문서화해 둔 Notion DB를 읽어 공지·안내 멘트를 즉시 초안 생성 | 흩어진 문서를 **재작성 없이 커뮤니케이션 자산으로** 재활용 |
| **Intercom + Slack MCP** | 오픈된 문의를 매일 자동 정리해 Slack에서 "무엇이 남았는지" 관리, 답변 초안까지 즉시 생성 | CS/유저 관리·운영을 **반자동화** — 사람은 검토·확정만 |
| **MCP (Model Context Protocol)** | Intercom · Slack · Notion 등 외부 도구를 AI에 직접 연결 | 코드 글루 없이 **AI가 실제 업무 시스템을 조작** |

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

### 4. 운명재판소 (Court of Destiny) — AI 판관 바이럴 모바일 게임
> 황당한 위기 상황 + 물품 2개가 주어지면 플레이어가 생존 계획을 쓰고, **AI 판관이 드라마틱하게 생사를 판정**하는 일회성 바이럴 모바일 게임. Google Play 비공개 테스트 가동 중.

- **스택:** Expo (React Native) · Supabase (Edge Functions · Postgres · 익명 Auth) · Gemini flash-lite *(provider 추상화 — Anthropic Haiku로 스왑 가능)* · AdMob · RevenueCat
- **🔥 AI 비용 엔지니어링 (핵심):** *"판당 흑자"*(광고수익 > AI 원가)를 위해 AI 호출 단가를 **0원에 근접하게 붕괴시키는 다계층 라우팅** 설계 — ① 판독불가 입력 차단 → ② `verdict_cache` 히트 → ③ 라이브 AI 호출(12초 타임아웃) → ④ 장애 시 **답안 룰베이스로 결과 정합한 프리셋 0원 강등** → ⑤ 최후 앱내 룰베이스. **어디서 막혀도 게임은 멈추지 않음.**
- **무인 운영 설계:** 콘텐츠=DB / 로직=OTA / 네이티브=고정 **3단 분리**로 스토어 재심사 최소화 · 서버 권위 토큰 캡으로 **바이럴 적자 방어** · 사건 683건 운영 중
- **왜 의미 있나:** AI를 *"쓰는"* 단계를 넘어 **AI 단가를 제품 경제성에 맞춰 설계**. 앱·백엔드·DB·토큰경제·광고·결제·스토어 배포까지 **혼자 end-to-end** 완성.

🔗 `Court-of-Destiny` *(비공개 / 데모 요청 가능)*

### 5. Tap-to-Sync — 숏폼 자막 싱크 자동화 MVP
> 숏폼 편집자가 **Tap 기반 UX + 자동 보정 엔진**으로 자막 싱크 시간을 크게 줄이는 Web MVP.

- **스택:** React · TypeScript · Vite · Tailwind CSS
- **핵심:** 재생 중 Tap/단축키로 timestamp 등록 → monotonic 보장·minGap·smoothing·길이 기반 분배 보정 → SRT / LRC / CapCut CSV 3종 export
- **왜 의미 있나:** 수동 창작 워크플로우를 **집중된 생산성 도구**로 전환한 제품 사고의 예시.

🔗 [`taptosync`](https://github.com/ZunaTtang/taptosync)

### 6. Live Archiver — 어려운 CLI를 내 입맛대로 만든 yt-dlp GUI
> **링크만 붙여넣고 "시작"** 누르면 라이브를 처음부터 아카이빙하는 브라우저 GUI. 강력하지만 쓰기 어려운 `yt-dlp` CLI를, 내가 실제로 쓰기 편한 도구로 직접 재설계한 결과물.

- **스택:** Python · JavaScript · Whisper(faster-whisper) · yt-dlp / ffmpeg 래핑
- **핵심:** `yt-dlp`/`ffmpeg`를 **OS에 맞게 자동 설치**(제로 셋업) · YouTube `--live-from-start`로 라이브 처음부터 수신 · 트위치·치지직·X 등 **1700+ 사이트** · 정지/복구 조각 처리 · **faster-whisper 전사**(GPU→CPU 폴백·이어하기 → SRT/TXT)
- **왜 의미 있나:** *"내가 쓰기 어려운 CLI를 내 워크플로우에 맞게 GUI로 바꾼다"* — 도구의 사용성을 직접 설계하는 **developer-experience / UX 감각**의 증거.

🔗 [`ytdlp-live-gui`](https://github.com/ZunaTtang/ytdlp-live-gui)

> **그 외:** Crypto Briefing Bot — 시장 데이터 수집 → Claude API 해석 → Telegram 자동 발송 파이프라인 ([`briefing-bot`](https://github.com/ZunaTtang/briefing-bot)) · Web Screenshot Autobot — 로그인 지원 BFS 크롤러로 전체화면 스크린샷 자동 저장 ([`auto-screenshot-bot`](https://github.com/ZunaTtang/auto-screenshot-bot))

---

## ⚙️ 운영 자동화 & 데이터 도구

레포지토리로 따로 공개하진 않았지만, 실제 운영 현장에서 매일 쓰이는 반자동화 시스템들입니다.

### MCP 기반 유저 관리 · 운영 반자동화
- **Notion MCP × Claude** — 기존에 문서화해 둔 Notion DB를 읽어, 공지·안내 멘트를 손쉽게 초안 생성. 매번 처음부터 쓰지 않고 **축적된 문서를 그대로 커뮤니케이션 자산으로** 활용.
- **Intercom MCP × Slack** — 현재 오픈된 문의를 읽어 **매일 자동으로 Slack에서 "무엇이 남았는지" 관리**하고, 답변 초안을 빠르게 생성해 담당자가 검토 후 직접 입력. CS·유저 관리·운영 업무를 **Human-in-the-loop 반자동화**로 전환.
- **왜 의미 있나:** 운영의 핵심 통증인 *"놓친 문의"* 와 *"매번 다시 쓰는 멘트"* 를 동시에 제거. AI가 1차 처리, 사람이 판단·확정.

### 레어 데이터 관리 (SQLite)
- 레어(rare) 데이터를 **SQLite로 가볍게 생성·관리** — 무거운 DB 인프라 없이 로컬에서 즉시 조회·갱신 가능한 데이터 레이어 구축.
- **왜 의미 있나:** 작은 데이터셋에 과한 인프라를 붙이지 않는 **적정 기술 선택** 감각.

### 거래소/DEX 자산 집계 자동화 (Google Apps Script)
- **Google Apps Script**로 거래소 API와 DEX RPC 서버에 접근해 자산 잔고를 불러오고, **Google 스프레드시트에 자동으로 정리**.
- **왜 의미 있나:** 별도 서버 없이 스프레드시트만으로 동작하는 **무인프라 자산 대시보드** — CEX·온체인 데이터를 한 시트에서 통합 관리.

---

## 🧰 핵심 역량

**AI & 자동화**
`Claude Code (Judge/Routines)` · `Claude API` · `Gemini` · `OpenAI API` · `Whisper 전사` · `MCP (Notion·Intercom·Slack)` · `AI 비용 최적화·다계층 라우팅` · `프롬프트 기반 프로세스 자동화` · `Human-in-the-loop 설계`

**프로덕트 & 그로스 옵스**
`캠페인 운영` · `유저 행동 분석` · `CRM/CS 워크플로우` · `CS 문의 반자동 응대` · `퍼널 모니터링` · `그로스 실험 운영` · `커뮤니티 자동화`

**기술 스택**
`TypeScript` · `Python` · `React / Next.js` · `React Native / Expo` · `Node.js` · `Supabase (Edge Functions·Postgres)` · `PostgreSQL / Prisma` · `SQLite` · `Google Apps Script` · `Playwright` · `Docker` · `GCP` · `REST / Webhook` · `Slack / Telegram / Intercom / Notion 연동`

**데이터 & 신호**
`Amplitude` · `운영 메트릭` · `QA 신호 설계` · `시장 데이터 모니터링` · `거래소 API / DEX RPC 자산 집계` · `스프레드시트 자동화` · `리포팅 파이프라인`

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
| **AI cost engineering** | Court of Destiny — **multi-tier routing** (cache · presets · rule-based fallback) collapses AI call cost toward zero | Designed an **AI economy** that stays *"profitable per play"* (provider-abstracted model swap) |
| **Claude API** | Turns crypto market data into expert-level briefings | Data ingest + AI interpretation + auto-delivery as **one content pipeline** |
| **Notion MCP** | Reads my existing documented Notion DBs to instantly draft announcements & user-facing copy | Reuses scattered docs as **comms assets — no rewriting** |
| **Intercom + Slack MCP** | Auto-triages open tickets into Slack daily ("what's still open?") and drafts replies on the spot | **Semi-automates** CS / user ops — humans just review & confirm |
| **MCP (Model Context Protocol)** | Connects Intercom, Slack, Notion, etc. directly to the AI | The **AI operates real business systems** without glue code |

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

### 4. Court of Destiny — AI-Judge Viral Mobile Game
> Given an absurd crisis + two items, the player writes a survival plan and an **AI judge dramatically rules life or death.** A one-shot viral mobile game, currently in Google Play closed testing.

- **Stack:** Expo (React Native) · Supabase (Edge Functions · Postgres · anon Auth) · Gemini flash-lite *(provider-abstracted — swappable to Anthropic Haiku)* · AdMob · RevenueCat
- **🔥 AI cost engineering (the core):** To stay *"profitable per play"* (ad revenue > AI cost), I designed **multi-tier routing that collapses AI call cost toward zero** — ① block unreadable input → ② `verdict_cache` hit → ③ live AI call (12s timeout) → ④ on failure, **rule-based evaluation downgrades to an answer-consistent preset at $0** → ⑤ last-resort in-app rules. **The game never stalls, wherever it breaks.**
- **Zero-ops design:** content=DB / logic=OTA / native=frozen **three-way split** minimizes store re-reviews · server-authoritative token caps **defend against a viral-driven loss** · 683 live scenarios
- **Why it matters:** Beyond *"using"* AI — I **engineer AI unit cost to fit product economics.** Built the app, backend, DB, token economy, ads, payments, and store release **solo, end-to-end.**

🔗 `Court-of-Destiny` *(private — demo available on request)*

### 5. Tap-to-Sync — Short-form Subtitle Sync MVP
> A web MVP that slashes subtitle-syncing time for short-form editors via a **tap-based UX + auto-correction engine.**

- **Stack:** React · TypeScript · Vite · Tailwind CSS
- **Core:** tap/hotkey timestamps during playback → monotonic guarantee, minGap, smoothing, length-based distribution → export to SRT / LRC / CapCut CSV
- **Why it matters:** Product thinking that converts a manual creative workflow into a focused productivity tool.

🔗 [`taptosync`](https://github.com/ZunaTtang/taptosync)

### 6. Live Archiver — a yt-dlp GUI rebuilt to fit my own workflow
> **Paste a link, hit "Start,"** and it archives a livestream from the very beginning — a browser GUI for the powerful-but-painful `yt-dlp` CLI, redesigned into a tool I actually enjoy using.

- **Stack:** Python · JavaScript · Whisper (faster-whisper) · yt-dlp / ffmpeg wrapping
- **Core:** **auto-installs** `yt-dlp`/`ffmpeg` per OS (zero setup) · YouTube `--live-from-start` capture · **1700+ sites** (Twitch, Chzzk, X, …) · stop/resume segment recovery · **faster-whisper transcription** (GPU→CPU fallback · resumable → SRT/TXT)
- **Why it matters:** *"I take a CLI I find hard to use and reshape it into a GUI that fits my workflow"* — evidence of **developer-experience / UX instinct**, designing usability firsthand.

🔗 [`ytdlp-live-gui`](https://github.com/ZunaTtang/ytdlp-live-gui)

> **Also:** Crypto Briefing Bot — collects market data → interprets via the Claude API → auto-sends to Telegram ([`briefing-bot`](https://github.com/ZunaTtang/briefing-bot)) · Web Screenshot Autobot — login-aware BFS crawler that auto-captures full-page screenshots ([`auto-screenshot-bot`](https://github.com/ZunaTtang/auto-screenshot-bot))

---

## ⚙️ Operational Automation & Data Tools

Not published as standalone repos, but real semi-automated systems used in day-to-day operations.

### MCP-based User Management & Ops Semi-automation
- **Notion MCP × Claude** — reads my already-documented Notion DBs to draft announcements and user-facing copy effortlessly. Instead of writing from scratch, **accumulated docs become reusable comms assets.**
- **Intercom MCP × Slack** — reads currently open tickets and **manages "what's still open?" in Slack automatically every day**, drafting replies fast so an operator reviews and sends. Turns CS / user management / ops into **human-in-the-loop semi-automation.**
- **Why it matters:** Kills two core ops pains at once — *missed tickets* and *re-writing the same copy*. AI does the first pass; humans judge and confirm.

### Rare-Data Management (SQLite)
- Spins up and manages rare datasets **lightly with SQLite** — an instantly queryable local data layer with no heavy DB infra.
- **Why it matters:** A sense for **right-sized tech** — not bolting overkill infrastructure onto small datasets.

### Exchange/DEX Asset Aggregation (Google Apps Script)
- Uses **Google Apps Script** to hit exchange APIs and DEX RPC endpoints, pull asset balances, and **auto-organize them into Google Sheets.**
- **Why it matters:** An **infra-free asset dashboard** running entirely in a spreadsheet — CEX + on-chain data unified in one sheet.

---

## 🧰 Core Capabilities

**AI & Automation** — `Claude Code (Judge/Routines)` · `Claude API` · `Gemini` · `OpenAI API` · `Whisper transcription` · `MCP (Notion·Intercom·Slack)` · `AI cost optimization / multi-tier routing` · `prompt-based process automation` · `human-in-the-loop design`

**Product & Growth Ops** — `campaign operations` · `user behavior analysis` · `CRM/CS workflows` · `semi-automated CS responses` · `funnel monitoring` · `growth experiments` · `community automation`

**Technical** — `TypeScript` · `Python` · `React / Next.js` · `React Native / Expo` · `Node.js` · `Supabase (Edge Functions·Postgres)` · `PostgreSQL / Prisma` · `SQLite` · `Google Apps Script` · `Playwright` · `Docker` · `GCP` · `REST / Webhooks` · `Slack / Telegram / Intercom / Notion integrations`

**Data & Signals** — `Amplitude` · `operational metrics` · `QA signal design` · `market data monitoring` · `exchange API / DEX RPC asset aggregation` · `spreadsheet automation` · `reporting pipelines`

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
