# AI Project OS Starter

AI와 함께 제품을 만들 때 **코드부터 시작하지 않고, 프로젝트가 어떻게 판단하고 실행될지 먼저 설정하는 예시 저장소**입니다.

이 저장소는 특정 서비스를 실제 출시하기 위한 코드베이스가 아니라, 교육을 위한 **완성형 프로젝트 셋업 샘플**입니다. 가상의 제품 `LinkPocket`을 예시로 사용합니다.

> 핵심 아이디어: AI에게 좋은 결과를 기대하기 전에, 제품 방향·정책·기술 선택·역할·작업 규칙·QA 기준을 먼저 설치한다.

## 예시 프로젝트: LinkPocket

LinkPocket은 사용자가 웹에서 발견한 링크를 저장하고, 제목·카테고리·메모로 다시 찾을 수 있게 하는 작은 북마크 웹앱입니다.

이 제품을 일부러 단순하게 잡은 이유는 **제품 자체보다 프로젝트를 어떻게 세팅하는지**를 보기 위해서입니다.

## 이 저장소에서 배우는 것

1. 아이디어를 `PROJECT_BRIEF`로 고정하는 법
2. 제품 정책과 수익모델을 코드와 분리해서 관리하는 법
3. 앱/웹, 언어, 프레임워크, DB, 배포 수단을 선택하는 법
4. 폴더 구조와 아키텍처 경계를 먼저 정하는 법
5. Product / Research / Design / Dev / QA 역할을 나누는 법
6. AI 에이전트끼리 임의로 결정하지 않게 하는 Handoff 구조
7. Engineering Harness와 QA Harness를 만드는 법
8. Do / Don't와 최소 변경 원칙(Ponytail)을 프로젝트 규칙으로 넣는 법
9. 현재 상태와 과거 결정을 분리해서 관리하는 법
10. `Task → Implement → Test → Review → Done`을 추적 가능하게 만드는 법

## 먼저 읽을 순서

프로젝트를 처음 보는 사람과 AI Agent 모두 아래 순서로 읽습니다.

1. `AGENTS.md`
2. `PROJECT_INSTRUCTIONS.md`
3. `docs/00_PROJECT_BRIEF.md`
4. `docs/CURRENT.md`
5. 현재 Task / Issue
6. Task와 직접 관련된 Spec / Decision / Harness만 추가로 읽기

과거 문서를 전부 읽고 시작하지 않습니다. **현재 상태 → 필요한 근거만 읽는 방식**을 사용합니다.

## 구조

```text
ai-project-os-starter/
├─ README.md
├─ AGENTS.md
├─ PROJECT_INSTRUCTIONS.md
│
├─ docs/
│  ├─ 00_PROJECT_BRIEF.md
│  ├─ 01_PRODUCT_POLICY.md
│  ├─ 02_BUSINESS_MODEL.md
│  ├─ 03_TECH_STACK.md
│  ├─ 04_ARCHITECTURE.md
│  ├─ 05_AGENT_OPERATING_MODEL.md
│  ├─ 06_ENGINEERING_HARNESS.md
│  ├─ 07_QA_RELEASE_HARNESS.md
│  ├─ 08_DECISIONS.md
│  ├─ 09_DESIGN_SYSTEM.md
│  ├─ 10_RESEARCH_REFERENCE.md
│  └─ CURRENT.md
│
├─ .cursor/
│  └─ rules/
│     ├─ 00-project-core.mdc
│     ├─ 10-task-execution.mdc
│     ├─ 20-product-design.mdc
│     ├─ 30-engineering.mdc
│     ├─ 40-security.mdc
│     └─ 50-qa-release.mdc
│
└─ .github/
   ├─ ISSUE_TEMPLATE/
   │  ├─ task.md
   │  ├─ bug.md
   │  └─ decision-needed.md
   └─ pull_request_template.md
```

## Project OS를 한 문장으로

**제품이 무엇인지 정하고 → AI와 사람의 권한을 나누고 → 기술과 파일 구조를 고정하고 → Task 단위로 실행하고 → Harness로 검증하는 것.**

## Source of Truth 예시

| 종류 | 기준 문서 |
|---|---|
| 제품 방향 | `docs/00_PROJECT_BRIEF.md` |
| 현재 유효 정책 | `docs/01_PRODUCT_POLICY.md` |
| 사업 가설 | `docs/02_BUSINESS_MODEL.md` |
| 기술 선택 | `docs/03_TECH_STACK.md` |
| 코드 구조 | `docs/04_ARCHITECTURE.md` |
| Agent 역할/인계 | `docs/05_AGENT_OPERATING_MODEL.md` |
| 개발 품질 규칙 | `docs/06_ENGINEERING_HARNESS.md` |
| QA/Release 기준 | `docs/07_QA_RELEASE_HARNESS.md` |
| 결정 변경 이력 | `docs/08_DECISIONS.md` |
| 디자인 규칙 | `docs/09_DESIGN_SYSTEM.md` |
| 현재 상태 | `docs/CURRENT.md` |
| 실행 단위 | GitHub Issues |
| 실제 구현 근거 | Git / Commit / PR / Test |

## 중요한 원칙

- 문서가 많다고 좋은 시스템은 아닙니다. **각 문서의 역할이 겹치지 않아야 합니다.**
- 제품 정책을 개발 Agent가 임의로 바꾸지 않습니다.
- AI가 생성한 결과를 완료로 취급하지 않습니다. 테스트와 검수가 끝나야 완료입니다.
- 현재 Task와 관계없는 리팩터링을 하지 않습니다.
- 새 코드·새 파일·새 abstraction은 필요성이 확인된 뒤에만 추가합니다.
- 모호하면 추측하지 않고 `DECISION NEEDED`로 올립니다.
- `CURRENT.md`에는 최신 상태만 두고, 과거 이력은 Decision / Issue / Git에 남깁니다.

## 교육용 사용법

이 저장소를 그대로 정답처럼 복제하기보다, 새 프로젝트를 시작할 때 각 문서를 질문지처럼 사용하세요.

예를 들어 `00_PROJECT_BRIEF.md`의 내용을 자신의 프로젝트로 바꾸고, 그 결정에 맞춰 `PRODUCT_POLICY → BUSINESS_MODEL → TECH_STACK → ARCHITECTURE → AGENT MODEL → HARNESS` 순서로 채워나갑니다.

프로젝트가 작다면 문서를 합쳐도 됩니다. **중요한 것은 파일 개수가 아니라 판단 기준과 책임 경계를 명확하게 만드는 것**입니다.
