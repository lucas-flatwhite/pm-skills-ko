[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)
[![한국어](https://img.shields.io/badge/lang-한국어-blue?style=flat-square)](#)
[![Upstream](https://img.shields.io/badge/upstream-phuryn%2Fpm--skills-lightgrey?style=flat-square)](https://github.com/phuryn/pm-skills)

# PM Skills 한국어판: 더 나은 제품 의사결정을 위한 AI 운영 시스템

> 8개 플러그인에 걸쳐 65개의 PM 스킬과 36개의 체인 워크플로우. Claude Code, Cowork 등과 호환. 디스커버리부터 전략, 실행, 런칭, 성장까지.

![플러그인 개요](.docs/images/plugins-overview.webp)

Claude Code와 Cowork에 최적화. 스킬은 다른 AI 어시스턴트와도 호환됩니다.

중국어로 skills를 찾고 싶다면 [Skills宝](https://skilery.com)도 함께 참고할 수 있습니다.

> **원본**: [phuryn/pm-skills](https://github.com/phuryn/pm-skills) by [Paweł Huryn](https://www.productcompass.pm)
> **한국어 번역**: [lucas-flatwhite/pm-skills-ko](https://github.com/lucas-flatwhite/pm-skills-ko)

## 목차

- [시작하기](#시작하기)
- [왜 PM Skills인가?](#왜-pm-skills인가)
- [작동 방식 (스킬, 커맨드, 플러그인)](#작동-방식-스킬-커맨드-플러그인)
- [설치](#설치)
- [사용 가능한 플러그인](#사용-가능한-플러그인)
- [업스트림 동기화](#업스트림-동기화)
- [검증](#검증)
- [기여 안내](#기여-안내)
- [Windows 알려진 문제](#windows-알려진-문제)
- [원작자](#원작자)
- [라이선스](#라이선스)

## 시작하기

> 먼저 [설치](#설치)를 완료한 후 아래 커맨드를 사용하세요.

| 상황 | 커맨드 |
| --- | --- |
| 새 아이디어? | `/discover` |
| 전략적 방향이 필요? | `/strategy` |
| PRD 작성? | `/write-prd` |
| 런칭 계획? | `/plan-launch` |
| 메트릭 정의? | `/north-star` |

## 왜 PM Skills인가?

일반 AI는 텍스트를 생성합니다. PM Skills는 **구조화된 의사결정**을 제공합니다.

각 스킬에는 검증된 PM 프레임워크가 인코딩되어 있습니다 — 디스커버리, 가정 매핑, 우선순위 결정, 전략 — 그리고 단계별로 안내합니다. Teresa Torres, Marty Cagan, Alberto Savoia의 엄격한 방법론이 일상 워크플로우에 내장됩니다.

결과: 더 빠른 문서가 아닌, 더 나은 제품 의사결정.

## 작동 방식 (스킬, 커맨드, 플러그인)

**스킬**은 마켓플레이스의 구성 요소입니다. 각 스킬은 특정 PM 작업에 대한 도메인 지식, 분석 프레임워크, 또는 가이드된 워크플로우를 Claude에 제공합니다. 일부 스킬은 여러 커맨드가 공유하는 재사용 가능한 기반으로도 작동합니다.

스킬은 대화와 관련성이 있을 때 자동으로 로드됩니다 — 명시적 호출 불필요. 필요 시(예: 일반 지식보다 스킬 우선) `/plugin-name:skill-name` 또는 `/skill-name`으로 **스킬을 강제 로드**할 수 있습니다.

**커맨드**는 `/command-name`으로 호출하는 사용자 트리거 워크플로우입니다. 하나 이상의 스킬을 엔드-투-엔드 프로세스로 체인합니다. 예를 들어, `/discover`는 네 개의 스킬을 체인합니다: brainstorm-ideas → identify-assumptions → prioritize-assumptions → brainstorm-experiments.

**플러그인**은 관련 스킬과 커맨드를 설치 가능한 패키지로 묶습니다. 각 플러그인은 PM 도메인을 커버합니다 — 디스커버리, 전략, 실행 등. 마켓플레이스를 설치하면 8개 플러그인 모두 설치됩니다.

![스킬 작동 방식](.docs/images/how-skills-work.webp)

커맨드는 스킬을 사용합니다. 일부 스킬은 여러 커맨드에서 사용됩니다. 일부 스킬(예: `prioritization-frameworks`, `opportunity-solution-tree`)은 관련성이 있을 때마다 Claude가 참조하는 독립 레퍼런스입니다.

커맨드는 PM 워크플로우에 맞게 서로 연결되도록 설계되어 있습니다. 커맨드가 완료되면 다음 커맨드를 제안합니다.

## 설치

### Claude Cowork (비개발자 권장)

1. **Customize** 열기 (왼쪽 하단)
2. **Browse plugins** → **Personal** → **+** 이동
3. **Add marketplace from GitHub** 선택
4. 입력: `phuryn/pm-skills`

8개 플러그인 모두 자동 설치됩니다.

![PM Skills 설치 in Claude Cowork](.docs/images/pm-skills-install.gif)

### Claude Code (CLI)

```bash
# 1단계: 마켓플레이스 추가
claude plugin marketplace add phuryn/pm-skills

# 2단계: 개별 플러그인 설치
claude plugin install pm-toolkit@pm-skills
claude plugin install pm-product-strategy@pm-skills
claude plugin install pm-product-discovery@pm-skills
claude plugin install pm-market-research@pm-skills
claude plugin install pm-data-analytics@pm-skills
claude plugin install pm-marketing-growth@pm-skills
claude plugin install pm-go-to-market@pm-skills
claude plugin install pm-execution@pm-skills
```

### 다른 AI 어시스턴트 (스킬만)

`skills/*/SKILL.md` 파일은 범용 스킬 형식을 따르며 해당 형식을 지원하는 모든 도구에서 작동합니다. 커맨드(`/slash-commands`)는 Claude 전용입니다.

| 도구           | 사용 방법                              | 지원 범위 |
| -------------- | -------------------------------------- | --------- |
| **Gemini CLI** | 스킬 폴더를 `.gemini/skills/`에 복사   | 스킬만    |
| **OpenCode**   | 스킬 폴더를 `.opencode/skills/`에 복사 | 스킬만    |
| **Cursor**     | 스킬 폴더를 `.cursor/skills/`에 복사   | 스킬만    |
| **Codex CLI**  | 스킬 폴더를 `.codex/skills/`에 복사    | 스킬만    |
| **Kiro**       | 스킬 폴더를 `.kiro/skills/`에 복사     | 스킬만    |

```bash
# 예시: OpenCode용 모든 스킬 복사 (프로젝트 레벨)
for plugin in pm-*/; do
  mkdir -p .opencode/skills/
  cp -r "$plugin/skills/"* .opencode/skills/ 2>/dev/null
done

# 예시: Gemini CLI용 모든 스킬 복사 (전역)
for plugin in pm-*/; do
  cp -r "$plugin/skills/"* ~/.gemini/skills/ 2>/dev/null
done
```

---

## 사용 가능한 플러그인

<details>
<summary><strong>1. pm-product-discovery</strong> — 아이디에이션, 실험, 가정 테스트, OST, 인터뷰 (13개 스킬, 5개 커맨드)</summary>

**스킬 (13):**

- `brainstorm-ideas-existing` — 기존 제품의 다관점 아이디에이션 (PM, 디자이너, 엔지니어)
- `brainstorm-ideas-new` — 초기 디스커버리 단계의 신규 제품 아이디에이션
- `brainstorm-experiments-existing` — 기존 제품의 가정 검증 실험 설계
- `brainstorm-experiments-new` — 신규 제품의 린 스타트업 프리타입 설계 (Alberto Savoia)
- `identify-assumptions-existing` — 가치, 사용성, 실행가능성, 실현가능성에 걸친 리스크 가정 식별
- `identify-assumptions-new` — GTM, 전략, 팀 등 8개 리스크 카테고리에 걸친 가정 식별
- `prioritize-assumptions` — Impact × Risk 매트릭스로 가정 우선순위 결정 및 실험 제안
- `prioritize-features` — 임팩트, 노력, 리스크, 전략적 정합성 기반 기능 백로그 우선순위 결정
- `analyze-feature-requests` — 테마와 전략적 적합성별 고객 기능 요청 분석 및 분류
- `opportunity-solution-tree` — Opportunity Solution Tree 구축 (Teresa Torres) — 아웃컴 → 기회 → 솔루션 → 실험
- `interview-script` — JTBD 탐침 질문이 포함된 구조화된 고객 인터뷰 스크립트 작성
- `summarize-interview` — 인터뷰 트랜스크립트를 JTBD, 만족 시그널, 액션 아이템으로 정리
- `metrics-dashboard` — 노스 스타, 인풋 메트릭, 알림 임계값으로 제품 메트릭 대시보드 설계

**커맨드 (5):**

- `/discover` — 풀 디스커버리 사이클: 아이디에이션 → 가정 매핑 → 우선순위 결정 → 실험 설계
- `/brainstorm` — 다관점 아이디에이션 (`ideas|experiments` × `existing|new`)
- `/triage-requests` — 기능 요청 배치 분석 및 우선순위 결정
- `/interview` — 인터뷰 스크립트 준비 또는 트랜스크립트 정리 (`prep|summarize`)
- `/setup-metrics` — 제품 메트릭 대시보드 설계

**예시:**

스킬:

- `AI 글쓰기 어시스턴트 아이디어의 가장 위험한 가정은?`
- `유저 활성화 개선을 위한 Opportunity Solution Tree 만들어줘`
- `엔터프라이즈 고객의 기능 요청 12개 우선순위 결정해줘 [CSV 첨부]`

커맨드:

- `/discover 원격 팀을 위한 AI 기반 미팅 요약 도구`
- `/brainstorm experiments existing — 온보딩 플로우에서 이탈률 줄여야 함`
- `/interview prep — 구매 프로세스에 대해 엔터프라이즈 구매자 인터뷰 예정`

</details>

<details>
<summary><strong>2. pm-product-strategy</strong> — 비전, 비즈니스 모델, 가격 전략, 경쟁 환경 (12개 스킬, 5개 커맨드)</summary>

제품 전략, 비전, 비즈니스 모델, 가격 전략, 거시 환경 분석. 비전 수립부터 경쟁 환경 스캔까지 전체 전략 툴킷을 커버합니다.

**스킬 (12):**

- `product-strategy` — 9섹션 제품 전략 캔버스 (비전 → 방어가능성)
- `startup-canvas` — 제품 전략(9섹션) + 비즈니스 모델을 결합한 스타트업 캔버스
- `product-vision` — 영감을 주는, 달성 가능한, 감성적인 제품 비전 작성
- `value-proposition` — 6파트 JTBD 가치 제안 (Who, Why, What before, How, What after, Alternatives)
- `lean-canvas` — 스타트업과 신제품을 위한 Lean Canvas 비즈니스 모델
- `business-model` — 9개 빌딩 블록을 포함한 Business Model Canvas
- `monetization-strategy` — 3~5개 수익화 전략 브레인스토밍 및 검증 실험
- `pricing-strategy` — 가격 모델, 경쟁사 분석, 지불 의사, 가격 탄력성
- `swot-analysis` — 실행 가능한 권고사항을 포함한 SWOT 분석
- `pestle-analysis` — 거시 환경 분석: 정치, 경제, 사회, 기술, 법률, 환경
- `porters-five-forces` — 경쟁 세력 분석 (경쟁 강도, 공급자, 구매자, 대체재, 신규 진입자)
- `ansoff-matrix` — 시장과 제품에 걸친 성장 전략 매핑

**커맨드 (5):**

- `/strategy` — 완전한 9섹션 제품 전략 캔버스 작성
- `/business-model` — 비즈니스 모델 탐색 (`lean|full|startup|value-prop|all`)
- `/value-proposition` — 6파트 JTBD 템플릿으로 가치 제안 설계
- `/market-scan` — SWOT + PESTLE + Porter's + Ansoff 결합 거시 환경 분석
- `/pricing` — 경쟁사 분석 및 실험을 포함한 가격 전략 설계

**예시:**

스킬:

- `마켓플레이스 스타트업에서 Lean Canvas vs Business Model Canvas vs Startup Canvas 비교`
- `비영어권 화자를 타겟으로 한 AI 글쓰기 어시스턴트의 가치 제안 설계`
- `프로젝트 관리 SaaS 시장에 대한 Porter's Five Forces 분석`

커맨드:

- `/strategy 에이전시를 위한 B2B 프로젝트 관리 툴`
- `/business-model startup — 비영어권 화자를 위한 AI 글쓰기 툴`
- `/value-proposition 엔터프라이즈 고객을 위한 SaaS 온보딩 툴`

</details>

<details>
<summary><strong>3. pm-execution</strong> — PRD, OKR, 로드맵, 스프린트, 레트로, 릴리즈 노트, 이해관계자 관리 (15개 스킬, 10개 커맨드)</summary>

일상적인 제품 관리: PRD, OKR, 로드맵, 스프린트, 레트로스펙티브, 릴리즈 노트, 프리모텀, 이해관계자 관리, 유저 스토리, 우선순위 결정 프레임워크.

**스킬 (15):**

- `create-prd` — 8섹션 PRD 종합 템플릿
- `brainstorm-okrs` — 회사 목표에 정렬된 팀 레벨 OKR
- `outcome-roadmap` — 기능 목록을 아웃컴 중심 로드맵으로 전환
- `sprint-plan` — 용량 추정, 스토리 선택, 리스크 식별이 포함된 스프린트 플래닝
- `retro` — 구조화된 스프린트 레트로스펙티브 진행
- `release-notes` — 티켓, PRD, 체인지로그에서 사용자 대상 릴리즈 노트 작성
- `pre-mortem` — Tigers/Paper Tigers/Elephants 분류를 통한 리스크 분석
- `stakeholder-map` — Power × Interest 그리드 및 맞춤형 커뮤니케이션 계획
- `summarize-meeting` — 미팅 트랜스크립트 → 결정사항 + 액션 아이템
- `user-stories` — 3C와 INVEST 기준을 따르는 유저 스토리
- `job-stories` — 잡 스토리: When [상황], I want to [동기], so I can [결과]
- `wwas` — Why-What-Acceptance 형식의 제품 백로그 아이템
- `test-scenarios` — 테스트 시나리오: 해피 패스, 엣지 케이스, 에러 처리
- `dummy-dataset` — CSV, JSON, SQL, Python 형식의 실제적인 더미 데이터셋
- `prioritization-frameworks` — 9개 우선순위 결정 프레임워크 레퍼런스 (Opportunity Score, ICE, RICE, MoSCoW, Kano 등)

**커맨드 (10):**

- `/write-prd` — 기능 아이디어나 문제 정의에서 PRD 작성
- `/plan-okrs` — 팀 레벨 OKR 브레인스토밍
- `/transform-roadmap` — 기능 중심 로드맵을 아웃컴 중심으로 전환
- `/sprint` — 스프린트 라이프사이클 (`plan|retro|release`)
- `/pre-mortem` — PRD나 런칭 계획의 프리모텀 리스크 분석
- `/meeting-notes` — 미팅 트랜스크립트를 구조화된 노트로 정리
- `/stakeholder-map` — 이해관계자 맵핑 및 커뮤니케이션 계획 수립
- `/write-stories` — 기능을 백로그 아이템으로 분해 (`user|job|wwa`)
- `/test-scenarios` — 유저 스토리에서 테스트 시나리오 생성
- `/generate-data` — 실제적인 더미 데이터셋 생성

**예시:**

스킬:

- `50개 백로그에 어떤 우선순위 결정 프레임워크를 사용해야 할까?`
- `플랫폼 마이그레이션 프로젝트의 이해관계자 맵핑`
- `Opportunity Score, ICE, RICE의 차이점은?`

커맨드:

- `/write-prd 알림 피로를 줄이는 스마트 알림 시스템`
- `/sprint retro — 지난 스프린트 노트입니다`
- `/write-stories job — "팀 대시보드" 기능을 잡 스토리로 분해`

</details>

<details>
<summary><strong>4. pm-market-research</strong> — 페르소나, 세분화, 여정 맵, 시장 규모, 경쟁사 분석 (7개 스킬, 3개 커맨드)</summary>

유저 리서치 및 경쟁사 분석: 페르소나, 세분화, 여정 맵, 시장 규모, 경쟁사 분석, 피드백 분석.

**스킬 (7):**

- `user-personas` — 리서치 데이터에서 정제된 유저 페르소나 작성
- `market-segments` — 인구통계, JTBD, 제품 적합성을 포함한 3~5개 고객 세그먼트 식별
- `user-segmentation` — 행동, JTBD, 니즈 기반 피드백 데이터에서 유저 세분화
- `customer-journey-map` — 단계, 터치포인트, 감정, 페인포인트를 포함한 엔드투엔드 여정 맵
- `market-sizing` — 탑다운 및 보텀업 접근법으로 TAM, SAM, SOM 산출
- `competitor-analysis` — 경쟁사 강점, 약점, 차별화 기회
- `sentiment-analysis` — 유저 피드백의 감성 분석 및 테마 추출

**커맨드 (3):**

- `/research-users` — 페르소나 구축, 유저 세분화, 고객 여정 맵핑
- `/competitive-analysis` — 경쟁 환경 분석
- `/analyze-feedback` — 유저 피드백의 감성 분석 및 세그먼트 인사이트

**예시:**

스킬:

- `미국 시장의 AI 코드 리뷰 툴에 대한 TAM/SAM/SOM 추정`
- `이커머스 체크아웃 플로우의 고객 여정 맵 작성`
- `행동과 니즈로 설문 응답자 세분화 [CSV 첨부]`

커맨드:

- `/research-users 피트니스 앱의 유저 12명 인터뷰 데이터가 있습니다`
- `/competitive-analysis 디자인 툴 분야의 Figma 경쟁사`
- `/analyze-feedback Q4 NPS 응답 200개입니다 [파일 첨부]`

</details>

<details>
<summary><strong>5. pm-data-analytics</strong> — SQL 생성, 코호트 분석, A/B 테스트 분석 (3개 스킬, 3개 커맨드)</summary>

PM을 위한 데이터 분석: SQL 쿼리 생성, 코호트 분석, A/B 테스트 분석.

**스킬 (3):**

- `sql-queries` — 자연어에서 SQL 생성 (BigQuery, PostgreSQL, MySQL)
- `cohort-analysis` — 코호트별 리텐션 커브, 기능 도입, 참여 트렌드
- `ab-test-analysis` — 통계적 유의성, 샘플 크기 검증, ship/extend/stop 권고

**커맨드 (3):**

- `/write-query` — 자연어에서 SQL 쿼리 생성
- `/analyze-cohorts` — 유저 참여 데이터 코호트 분석
- `/analyze-test` — A/B 테스트 결과 분석

**예시:**

스킬:

- `95% 신뢰도에 2% MDE로 샘플 크기는 얼마나 필요한가?`
- `구독 앱에서 어떤 리텐션 메트릭을 추적해야 할까?`

커맨드:

- `/write-query Q4 2025 국가별 월간 활성 유저 수 보여줘 (BigQuery)`
- `/analyze-test 체크아웃 플로우 A/B 테스트 결과입니다 [CSV 첨부]`
- `/analyze-cohorts 1월 vs 2월 가입 유저의 주간 리텐션`

</details>

<details>
<summary><strong>6. pm-go-to-market</strong> — 비치헤드 세그먼트, ICP, 메시징, 성장 루프, GTM 모션, 배틀카드 (6개 스킬, 3개 커맨드)</summary>

GTM 전략: 비치헤드 세그먼트, 이상적 고객 프로필(ICP), 메시징, 성장 루프, GTM 모션, 영업 배틀카드.

**스킬 (6):**

- `gtm-strategy` — 전체 GTM 전략: 채널, 메시징, 성공 메트릭, 런칭 계획
- `beachhead-segment` — 첫 번째 비치헤드 시장 세그먼트 식별
- `ideal-customer-profile` — 인구통계, 행동, JTBD, 니즈를 포함한 ICP
- `growth-loops` — 지속 가능한 성장 루프 설계 (플라이휠)
- `gtm-motions` — GTM 모션 및 도구 평가 (제품 주도, 영업 주도 등)
- `competitive-battlecard` — 이의 처리 및 승리 전략을 포함한 영업 준비 배틀카드

**커맨드 (3):**

- `/plan-launch` — 비치헤드부터 런칭 계획까지 전체 GTM 전략
- `/growth-strategy` — 성장 루프 설계 및 GTM 모션 평가
- `/battlecard` — 경쟁사 배틀카드 작성

**예시:**

스킬:

- `개발자 생산성 툴의 최적 비치헤드 세그먼트는?`
- `프리미엄 티어가 있는 B2B SaaS의 성장 루프 설계`
- `AI 기반 HR 스크리닝 플랫폼의 ICP 정의`

커맨드:

- `/plan-launch 중규모 엔지니어링 팀 타겟 AI 코드 리뷰 툴`
- `/battlecard SMB 시장에서 우리 CRM vs Salesforce`
- `/growth-strategy 프리랜서와 스타트업을 연결하는 양면 마켓플레이스`

</details>

<details>
<summary><strong>7. pm-marketing-growth</strong> — 마케팅 아이디어, 포지셔닝, 가치 제안, 네이밍, 노스 스타 메트릭 (5개 스킬, 2개 커맨드)</summary>

제품 마케팅 및 성장: 마케팅 아이디어, 포지셔닝, 가치 제안 문구, 제품 네이밍, 노스 스타 메트릭.

**스킬 (5):**

- `marketing-ideas` — 채널과 메시징을 포함한 창의적이고 비용 효율적인 마케팅 아이디어
- `positioning-ideas` — 경쟁사와 차별화된 제품 포지셔닝
- `value-prop-statements` — 마케팅, 영업, 온보딩을 위한 가치 제안 문구
- `product-name` — 브랜드 가치와 타겟 오디언스에 맞는 제품 네이밍 브레인스토밍
- `north-star-metric` — 비즈니스 게임 분류를 포함한 노스 스타 메트릭 + 인풋 메트릭

**커맨드 (2):**

- `/market-product` — 마케팅 아이디어, 포지셔닝, 가치 제안, 제품명 브레인스토밍
- `/north-star` — 노스 스타 메트릭 및 지원 인풋 메트릭 정의

**예시:**

스킬:

- `Notion과 차별화하는 5가지 포지셔닝 앵글 브레인스토밍`
- `양면 마켓플레이스의 좋은 노스 스타 메트릭은?`
- `영업팀 피치덱용 가치 제안 문구 생성`

커맨드:

- `/market-product 이커머스 매니저를 위한 B2B 분석 대시보드`
- `/north-star 프리랜서와 클라이언트를 연결하는 양면 마켓플레이스`

</details>

<details>
<summary><strong>8. pm-toolkit</strong> — 이력서 검토, 법률 문서, 교정 (4개 스킬, 5개 커맨드)</summary>

핵심 제품 업무 외 PM 유틸리티: 이력서 검토, 법률 문서, 교정.

**스킬 (4):**

- `review-resume` — PM 이력서 검토 및 10가지 베스트 프랙티스에 맞춘 조정 (XYZ+S 공식, 키워드, 구조)
- `draft-nda` — 관할권에 적합한 조항을 포함한 비밀유지계약서(NDA)
- `privacy-policy` — GDPR/CCPA 컴플라이언스를 커버하는 개인정보처리방침
- `grammar-check` — 문법, 논리, 흐름 검토 및 타겟 수정

**커맨드 (5):**

- `/review-resume` — 종합 PM 이력서 검토
- `/tailor-resume` — 특정 채용공고에 맞게 이력서 조정
- `/draft-nda` — NDA 초안 작성
- `/privacy-policy` — 개인정보처리방침 초안 작성
- `/proofread` — 문법, 논리, 흐름 검토

**예시:**

스킬:

- `PM 이력서를 베스트 프랙티스에 맞게 검토해줘 [PDF 첨부]`
- `제품 발표문의 문법과 명확성 확인`

커맨드:

- `/review-resume [PM 이력서 첨부]`
- `/tailor-resume [이력서 + 채용공고 붙여넣기]`
- `/proofread Q1 투자자 업데이트 초안입니다`

</details>

---

## 업스트림 동기화

원본 저장소([phuryn/pm-skills](https://github.com/phuryn/pm-skills))의 새 스킬을 추적하고 번역에 반영합니다:

```bash
git fetch upstream
git diff upstream/main -- pm-product-discovery/skills/new-skill/SKILL.md
# 새 스킬 발견 시 → 번역 후 추가
```

## 검증

```bash
python3 validate_plugins.py
```

## 기여 안내

[CONTRIBUTING.md](CONTRIBUTING.md)를 참조하세요.

## Windows 알려진 문제

Cowork가 불안정하여 VM을 시작할 수 없는 경우 ([claude-code/issues/27010](https://github.com/anthropics/claude-code/issues/27010)), 다음을 시도하세요:

```powershell
$action = New-ScheduledTaskAction -Execute "powershell.exe" -Argument "-WindowStyle Hidden -Command `"if ((Get-Service CoworkVMService).Status -ne 'Running') { Start-Service CoworkVMService }`""
$trigger = New-ScheduledTaskTrigger -RepetitionInterval (New-TimeSpan -Minutes 1) -Once -At (Get-Date)
$settings = New-ScheduledTaskSettingsSet -AllowStartIfOnBatteries -DontStopIfGoingOnBatteries
Register-ScheduledTask -TaskName "CoworkVMServiceMonitor" `
  -Action $action `
  -Trigger $trigger `
  -Settings $settings `
  -RunLevel Highest `
  -User "SYSTEM"
```

이 방법으로 Windows 문제의 90%가 해결됩니다.

나머지 10%: services.msc를 열고 "Claude" 서비스를 수동으로 시작하세요.

## 원작자

이 마켓플레이스는 [Paweł Huryn](https://www.productcompass.pm)의 원본 작업을 기반으로 합니다.

스킬 선정 기반 참고 문헌:

- Teresa Torres — [_Continuous Discovery Habits_](https://www.amazon.com/Continuous-Discovery-Habits-Discover-Products/dp/1736633309/)
- Marty Cagan — [_INSPIRED_](https://www.amazon.com/INSPIRED-Create-Tech-Products-Customers/dp/1119387507/) 및 [_TRANSFORMED_](https://www.amazon.com/dp/1119697336/)
- Alberto Savoia — [_The Right It_](https://www.amazon.com/Right-Many-Ideas-Yours-Succeed/dp/0062884654)
- Dan Olsen — [_The Lean Product Playbook_](https://www.amazon.com/dp/1118960874/)
- Roger L. Martin — [_Playing to Win_](https://www.amazon.com/Playing-Win-Expanded-Bonus-Articles/dp/B0F25SDYWV/)
- Ash Maurya — [_Running Lean_](https://www.amazon.com/dp/B004J4XGN6/)
- Strategyzer — [_Business Model Generation_](https://www.amazon.com/dp/0470876417/) 및 [_Value Proposition Design_](https://www.amazon.com/dp/1118968050/)
- Christina Wodtke — [_Radical Focus_](https://www.amazon.com/Radical-Focus-Achieving-Important-Objectives/dp/0996006052)
- Anthony W. Ulwick — [_Jobs to Be Done_](https://jobs-to-be-done-book.com/)
- Alistair Croll & Benjamin Yoskovitz — [_Lean Analytics_](https://www.amazon.com/Lean-Analytics-Better-Startup-Faster/dp/1449335675/)
- Sean Ellis — [_Hacking Growth_](https://www.amazon.com/Hacking-Growth-Fastest-Growing-Companies-Breakout/dp/045149721X/)
- Maja Voje — [_Go-To-Market Strategist_](https://gtmstrategist.com/)

Paweł Huryn이 [The Product Compass Newsletter](https://www.productcompass.pm)에서 큐레이션.

## 라이선스

MIT — [LICENSE](LICENSE) 참조.
