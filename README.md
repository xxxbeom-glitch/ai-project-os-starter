# AI Project OS Starter

이 저장소는 **ChatGPT Project, Claude Project, Cursor 등 여러 AI 도구를 오가더라도 프로젝트의 방향과 실행 기준이 흔들리지 않게 만드는 교육용 Starter**입니다.

가상의 북마크 웹앱 `LinkPocket`을 예시로 사용합니다.

> 핵심 아이디어: AI의 기억에 프로젝트를 맡기지 않고, **제품의 중요한 판단은 기준 문서에, 작업은 Task / Issue에, 구현 증거는 Commit / Test에, 현재 위치는 CURRENT에 남긴다.**

## 이 Starter가 해결하려는 문제

AI와 프로젝트를 진행하다 보면 다음 문제가 쉽게 생깁니다.

- 대화마다 제품 방향이 조금씩 달라진다.
- ChatGPT와 Claude가 서로 다른 전제를 사용한다.
- 개발 AI가 제품 정책을 임의로 바꾼다.
- 왜 특정 기술이나 UX를 선택했는지 나중에 알기 어렵다.
- “구현 완료”라고 했지만 실제 테스트 근거가 없다.
- 프로젝트가 커질수록 결정과 작업 이력이 섞인다.

이 Starter는 이를 막기 위해 **Project Bootstrap → Project OS → Execution → QA**의 최소 운영 구조를 제공합니다.

## 두 가지 운영 모드

### 1. BOOTSTRAP MODE
실제 제작 전에 LLM이 사용자를 인터뷰해 제품의 초기 기준을 만드는 단계입니다.

`PROJECT_BOOTSTRAP.md`를 따라 다음을 정리합니다.

- Product / Target / Problem / MVP
- Policy
- Business Model
- Platform / Tech Stack
- Architecture 최소 기준
- Design 방향
- Role / Decision Gate
- Engineering / QA Harness

이 단계에서는 모든 논의를 GitHub Issue로 만들 필요가 없습니다.

### 2. EXECUTION MODE
`Project OS v0.1` 승인 후 실제 기획·디자인·개발을 진행하는 단계입니다.

기본 Traceability:

```text
Decision / Spec
↓
Task / GitHub Issue
↓
Implementation
↓
Commit / PR / Test Evidence
↓
Independent QA
↓
PASS → Close
↓
CURRENT update
```

코드 변경 Task는 GitHub Issue를 기본 실행 단위로 사용합니다.

## Canonical Source

**GitHub Repository 한 곳을 Canonical Source로 사용합니다.**

- GitHub = 최신 기준 문서와 실행 이력
- ChatGPT / Claude Project에 업로드한 파일 = Snapshot
- Cursor / 개발 도구 = 같은 GitHub Repository를 기준으로 작업

ChatGPT와 Claude에 같은 파일을 각각 올렸더라도 두 복사본을 독립적으로 발전시키지 않습니다. 중요한 결정은 GitHub 기준 문서에 반영합니다.

## 추천 구조

```text
ai-project-os-starter/
├─ README.md
├─ PROJECT_INSTRUCTIONS.md
├─ PROJECT_BOOTSTRAP.md
├─ PROJECT_FOLDER_SETUP.md
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
├─ roles/
│  ├─ PRODUCT_PM.md
│  ├─ RESEARCH.md
│  ├─ DESIGN.md
│  ├─ DEVELOPMENT.md
│  └─ QA.md
│
└─ templates/
   ├─ TASK.md
   ├─ HANDOFF.md
   ├─ DECISION.md
   └─ QA_REPORT.md
```

## 핵심 파일

| 파일 | 역할 |
|---|---|
| `PROJECT_INSTRUCTIONS.md` | 모든 AI가 지켜야 하는 공통 운영 규칙 |
| `PROJECT_BOOTSTRAP.md` | 새 프로젝트를 인터뷰로 초기화하는 절차 |
| `PROJECT_FOLDER_SETUP.md` | ChatGPT / Claude / GitHub에서 실제로 사용하는 방법 |
| `00_PROJECT_BRIEF.md` | 무엇을 왜 만드는가 |
| `01_PRODUCT_POLICY.md` | 서비스 정책 |
| `02_BUSINESS_MODEL.md` | 수익모델과 검증할 사업 가설 |
| `03_TECH_STACK.md` | 무엇으로 만들 것인가 |
| `04_ARCHITECTURE.md` | 코드와 파일 책임을 어떻게 나눌 것인가 |
| `05_AGENT_OPERATING_MODEL.md` | Role과 Handoff 방식 |
| `06_ENGINEERING_HARNESS.md` | 개발 안전레일과 Git Traceability |
| `07_QA_RELEASE_HARNESS.md` | Evidence 기반 QA / Release Gate |
| `08_DECISIONS.md` | 왜 그렇게 결정했는가 |
| `09_DESIGN_SYSTEM.md` | 디자인 일관성 기준 |
| `10_RESEARCH_REFERENCE.md` | 조사와 레퍼런스 검증 규칙 |
| `CURRENT.md` | 지금 어디에 있고 다음은 무엇인가 |

## Role과 Tool은 분리한다

Role은 책임이고 Tool은 실행 수단입니다.

예:
- Product / PM
- Research
- Design
- Development
- QA

이 역할을 ChatGPT, Claude, Cursor 중 누가 맡을지는 프로젝트 상황과 도구 성능에 따라 바뀔 수 있습니다.

따라서 `ChatGPT = PM`, `Claude = QA`, `Cursor = Dev`처럼 영구 고정하지 않습니다.

## Git 작업 기록 원칙

Execution Mode에서는 **하나의 의미 있는 work cycle = 하나의 추적 가능한 Commit**을 기본값으로 합니다.

의미 있는 work cycle은 하나의 목적을 가진 검토·테스트 가능한 변경 단위입니다.

- 채팅 한 번마다 Commit하지 않습니다.
- 사소한 저장마다 Commit하지 않습니다.
- Commit / PR에서 Task / Issue를 역추적할 수 있어야 합니다.
- 작업 결과에는 Result / Tests / Commit / Risk / Not Verified를 남깁니다.
- QA PASS 이후 최종 DONE / Close를 판단합니다.

예:

```text
feat(#14): add bookmark deletion
fix(TSK-021): prevent duplicate save
```

GitHub Project Board, Sprint, Story Point 같은 복잡한 관리 체계는 실제 필요가 생길 때만 추가합니다.

## 처음 사용할 때

새 프로젝트를 시작한다면:

1. 이 Repository를 새 Repository로 복사한다.
2. ChatGPT 또는 Claude에게 전체 구조를 읽게 한다.
3. `PROJECT_BOOTSTRAP.md` 기준으로 사용자 인터뷰를 진행한다.
4. 예시 `LinkPocket` 내용을 실제 프로젝트 내용으로 교체한다.
5. 전체 문서를 교차 QA한다.
6. 사용자 승인 후 `Project OS v0.1`로 정리한다.
7. `CURRENT.md`에 첫 실행 Task를 적는다.
8. 실제 구현부터 GitHub Issue / Commit / Test / QA 추적을 시작한다.

## 최종 원칙

**문서를 많이 만드는 것이 목적이 아니다. 도구와 대화가 바뀌어도 같은 제품을 만들고, 무엇을 왜 바꿨는지 다시 추적할 수 있게 만드는 것이 목적이다.**
