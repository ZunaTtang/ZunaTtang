# 장필규 · Zuna

**운영을 직접 하던 사람이, 그 운영을 시스템으로 만듭니다.**

크립토 트레이딩 서비스 리그오브트레이더스에서 5년(2021.10 – 2026.11) 동안 CS·QA·이벤트·거래소 연동을 맡았고, 마지막에는 제가 하던 일을 봇과 에이전트에게 넘겼습니다.
직무 하나로 설명되지 않는 쪽입니다. 운영 자동화와 AI 에이전트, 모바일 앱과 웹 서비스, 혼자 쓰려고 만든 도구까지 기획부터 배포까지 직접 합니다.

`구직 중 · 2026.11~` · AX · Product Ops · Crypto

---

## 만든 것

### 앱 · 웹 서비스

| 프로젝트 | 무엇 | 스택 |
|---|---|---|
| **운명재판소** · [Google Play](https://play.google.com/store/apps/details?id=com.zunattang.fatetribunal) | AI 판관이 생존 계획의 생사를 판정하는 모바일 게임. 판당 광고 수익이 AI 원가보다 크도록 캐시·프리셋·폴백 라우팅 설계 | Expo · Supabase · Gemini · AdMob |
| **스팀 동접 버블맵** · [사이트](https://steambubbles.vercel.app) · [코드](https://github.com/ZunaTtang/steambubbles) | 스팀 게임의 동시접속과 할인을 버블맵 하나로. 상위 약 3,000개 게임을 무인 수집 | Next.js · PixiJS · Neon · QStash |
| **ClientBrief** · [코드](https://github.com/ZunaTtang/clientbrief) | GitHub 활동을 비개발자용 주간 리포트로 만들고 승인 후 메일 발송하는 SaaS | Next.js · Prisma · NextAuth |
| **Tap-to-Sync** · [코드](https://github.com/ZunaTtang/taptosync) | 재생 중 탭으로 숏폼 자막 싱크를 맞추고 SRT·CapCut으로 내보내는 웹 도구 | React · TypeScript |
| **Stealth Arcade** · [코드](https://github.com/ZunaTtang/stealth-arcade) | 뿌요뿌요·테트리스·스도쿠·지뢰찾기를 창 하나에. Esc 한 번에 사라짐 | Python · PyQt5 |

### 운영 자동화 · AI

| 프로젝트 | 무엇 | 스택 |
|---|---|---|
| **CS 에이전트** *(비공개)* | 인터컴 문의를 판단해 되묻기·개발 제보·최종 답장까지. 애매하면 사람에게 넘김. 개발 전달 건당 10분 → 1분 | Claude · Python · Intercom · Slack |
| **Intercom Daily Digest** · [코드](https://github.com/ZunaTtang/intercom-digest-routine) | 매일 아침 열린 문의를 우선순위별로 요약해 Slack에 게시 | Claude Code Routines · MCP |
| **Web QA 자동화** *(비공개)* | 빌드 간 회귀를 스냅샷으로 비교하고, 의심 케이스만 Claude가 판정 | Playwright · TypeScript · Claude |
| **Asset Check Bot** *(업무용)* | 거래소·지갑 잔고와 거래량을 매일 시트와 Slack으로. 매일 30분 수작업 → 0 | Apps Script · Cloud Run |
| **Briefing Bot** · [코드](https://github.com/ZunaTtang/briefing-bot) | 시장 데이터를 수집·해석해 텔레그램으로 매일 브리핑 | Claude API · Telegram |
| **Gmail → Slack Notifier** · [코드](https://github.com/ZunaTtang/gmail-to-slack-notifier) | 조건에 맞는 메일을 Slack 알림으로 | Apps Script |

### 나를 위한 도구

| 프로젝트 | 무엇 | 스택 |
|---|---|---|
| **Live Archiver** · [코드](https://github.com/ZunaTtang/ytdlp-live-gui) | 링크만 붙여넣으면 라이브를 처음부터 저장하고 자막까지. 쓰기 어려운 yt-dlp CLI를 GUI로 | Python · yt-dlp · Whisper |
| **Upbit Pocket Tester** · [코드](https://github.com/ZunaTtang/upbit-pocket-tester) | 업비트 Open API를 사람이 직접 호출해 검증하는 로컬 GUI | Python |
| **Auto Screenshot Bot** · [코드](https://github.com/ZunaTtang/auto-screenshot-bot) | 로그인 후 사이트 전체를 돌며 전체화면 스크린샷 저장 | Python · Playwright |

---

## AI와 일하는 방식

- **맡기기 전에 목표·원칙·완료 기준부터 정합니다.** "완전 무인화가 목표가 아니다. 명확한 것만 자동, 애매하면 HOLD."
- **실제 운영 데이터를 판단 근거로 넣습니다.** 2년치 CS 케이스, 한 달치 답장 말투, 실제로 겪은 장애.
- **결과를 그대로 믿지 않습니다.** 중간 산출물을 요구하고, 숫자는 역산해서 확인합니다.
- **권한은 한 단계씩 엽니다.** 테스트 계정 → 초안만 → 실전 1회 → 자동. 되돌릴 수 없는 발송은 사람이.
- **한 번 만든 건 남이 이어받게 남깁니다.** 스킬·루틴 지침, 유지보수 문서, CLI 대신 GUI.

## 숫자로

| 이전 → 이후 | 무엇 |
|---|---|
| 10분 → 1분 | 개발팀 CS 전달, 건당 |
| 30분 → 0 | 매일 하던 자산 확인 수작업 |
| 30분–2시간 → 5분 이내 | 영문 CS 첫 응답 (GPT 반자동) |
| 1시간 → 5분 | 캠페인 배너 세팅 |

## 쓰는 도구

`Claude Code` `Claude API` `MCP (Intercom · Slack · Notion · Figma)` `Gemini` `OpenAI`
`TypeScript` `Python` `Next.js` `React Native / Expo` `Supabase` `PostgreSQL` `Playwright`
`Google Apps Script` `Cloud Run` `Vercel` `Amplitude` `Intercom` `Mailchimp`

## 연락

GitHub [@ZunaTtang](https://github.com/ZunaTtang)

---

<details>
<summary><b>English</b></summary>

### Pilgyu Jang · Zuna

**I ran operations by hand, then turned them into systems.**

Five years (Oct 2021 – Nov 2026) at League of Traders, a crypto trading service: support, QA, events and exchange integrations, ending by handing my own job to bots and an agent. I'm a generalist: ops automation and AI agents, mobile apps and web services, and tools I build for myself, from planning to release. Open to work from Nov 2026 (AX · Product Ops · Crypto).

**Apps & web** — Court of Destiny, an AI-judge mobile game on [Google Play](https://play.google.com/store/apps/details?id=com.zunattang.fatetribunal) · [Steam Bubbles](https://steambubbles.vercel.app), a bubble map of Steam players and discounts · [ClientBrief](https://github.com/ZunaTtang/clientbrief), weekly GitHub reports for non-engineers · [Tap-to-Sync](https://github.com/ZunaTtang/taptosync) · [Stealth Arcade](https://github.com/ZunaTtang/stealth-arcade)

**Ops automation & AI** — a CS agent that triages, asks back, files bugs and replies, with humans kept on anything ambiguous (dev handoff 10 → 1 min) · [Intercom Daily Digest](https://github.com/ZunaTtang/intercom-digest-routine) · a Claude-judged web QA pipeline · an asset check bot (30 min/day of manual work → 0) · [Briefing Bot](https://github.com/ZunaTtang/briefing-bot) · [Gmail → Slack Notifier](https://github.com/ZunaTtang/gmail-to-slack-notifier)

**Tools for myself** — [Live Archiver](https://github.com/ZunaTtang/ytdlp-live-gui) · [Upbit Pocket Tester](https://github.com/ZunaTtang/upbit-pocket-tester) · [Auto Screenshot Bot](https://github.com/ZunaTtang/auto-screenshot-bot)

**How I work with AI** — set the goal, rules and "done" first · give it real operating data · verify the output and the numbers · open up permissions one step at a time · leave docs so others can take over.

</details>
