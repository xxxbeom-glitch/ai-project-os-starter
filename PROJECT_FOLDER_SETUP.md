# PROJECT FOLDER SETUP GUIDE

이 문서는 `PROJECT_INSTRUCTIONS.md`, `PROJECT_BOOTSTRAP.md`, `docs/` 파일을 **ChatGPT Project / Claude Project 같은 프로젝트형 AI 작업공간에서 어떻게 넣고 운영할지** 설명한다.

## 1. 제품 하나당 Project 하나

서로 다른 제품을 하나의 Project에 섞지 않는다.

예:
- LinkPocket
- 여행 예약 서비스
- 익명 커뮤니티 앱

## 2. GitHub를 Canonical Source로 둔다

이 Starter를 새 GitHub Repository로 복사한 뒤 그 Repository를 프로젝트의 **Canonical Source**로 사용한다.

- GitHub = 최종 기준 문서와 실행 이력
- ChatGPT / Claude Project에 업로드한 파일 = Snapshot
- Cursor 또는 다른 개발 도구 = 같은 Repository를 기준으로 작업

Snapshot을 각 플랫폼에서 독립적으로 발전시키지 않는다.

중요한 결정이나 수정이 생기면 GitHub 기준 문서에 반영하고, 필요하면 Project의 Snapshot을 다시 동기화한다.

## 3. 상위 지침을 넣는다

`PROJECT_INSTRUCTIONS.md`는 프로젝트 전체의 공통 행동 규칙이다.

플랫폼에 Project Instructions, Custom Instructions, Project Guidelines처럼 지속 지침을 넣을 수 있는 영역이 있다면 핵심 내용을 넣는다.

목적:
- 대화마다 제품 방향이 달라지는 것 방지
- 이미 정한 정책을 다시 뒤집는 것 방지
- 역할별 책임 혼선 방지
- 완료 기준 없는 작업 방지
- AI가 모르는 내용을 추측하는 것 방지

## 4. 새 프로젝트는 Bootstrap부터 시작한다

새 Repository를 만든 직후에는 `PROJECT_BOOTSTRAP.md`를 따른다.

LLM에게 Starter 전체 구조를 읽힌 뒤:

1. 예시 내용을 실제 요구사항으로 간주하지 않게 한다.
2. 사용자 인터뷰를 시작한다.
3. Product → Policy / Business → Tech → Design → Operating Model 순으로 정리한다.
4. 미확정 항목은 `CONFIRMED / ASSUMPTION / TBD / RESEARCH NEEDED`로 분리한다.
5. 전체 문서를 교차 QA한다.
6. 사용자 승인 후 `Project OS v0.1`로 정리한다.
7. `CURRENT.md`에 현재 상태와 첫 실행 Task를 적는다.

Bootstrap 중 모든 질문과 논의를 GitHub Issue로 만들 필요는 없다.

## 5. 기준 문서를 프로젝트 자료로 넣는다

`docs/`는 프로젝트의 공용 기준 문서다.

처음부터 모든 파일을 길게 만들 필요는 없다.

### 최소 시작 세트
- `00_PROJECT_BRIEF.md`
- `03_TECH_STACK.md`
- `05_AGENT_OPERATING_MODEL.md`
- `06_ENGINEERING_HARNESS.md`
- `CURRENT.md`

### 필요할 때 확장
- 정책 이슈가 생기면 `01_PRODUCT_POLICY.md`
- 수익화가 중요하면 `02_BUSINESS_MODEL.md`
- 구조가 복잡해지면 `04_ARCHITECTURE.md`
- 디자인 일관성이 필요하면 `09_DESIGN_SYSTEM.md`
- QA가 커지면 `07_QA_RELEASE_HARNESS.md`
- 결정이 쌓이면 `08_DECISIONS.md`

## 6. 역할은 Tool이 아니라 책임으로 나눈다

같은 Project 안에서 대화를 역할별로 나눌 수 있다.

예:
- Product / PM
- Research
- Design
- Development
- QA

ChatGPT, Claude, Cursor 중 어떤 도구가 어떤 역할을 맡을지는 고정하지 않는다.

모델이나 제품 기능은 바뀔 수 있기 때문에 **Role과 Tool을 분리**한다.

## 7. 별도 대화와 AI가 서로 기억한다고 가정하지 않는다

별도 대화, 별도 Agent, 별도 AI 서비스는 서로의 최신 대화를 자동 공유한다고 가정하면 안 된다.

중요한 결과는 파일 또는 GitHub 실행 이력으로 남긴다.

예:
- 정책 결정 → `08_DECISIONS.md` + `01_PRODUCT_POLICY.md`
- 디자인 기준 변경 → `09_DESIGN_SYSTEM.md`
- 기술 선택 변경 → `03_TECH_STACK.md` + `08_DECISIONS.md`
- 현재 상태 → `CURRENT.md`
- 구현 작업 → GitHub Issue / Commit / Test / QA

즉:

**대화 = 작업 공간**  
**기준 문서 = 제품 기억**  
**Issue / Task = 작업 기억**  
**Commit / Test = 구현 증거**  
**CURRENT = 현재 위치**

## 8. Bootstrap Mode와 Execution Mode

### Bootstrap Mode
제품의 방향과 운영 기준을 만드는 단계다.

Issue 관리보다 문서와 Decision 정합성이 우선이다.

### Execution Mode
Project OS v0.1 이후 실제 제작 단계다.

기본 흐름:

```text
Product / PM
↓ Task / GitHub Issue 정의
Research / Design
↓ 필요한 근거와 명세
Development
↓ 구현 + Test + Commit
QA
↓ PASS / FIX / DECISION NEEDED
Product / PM
↓ Issue Close + 기준 문서 / CURRENT 갱신
```

항상 모든 Role을 통과할 필요는 없다. 작업 위험도와 성격에 맞게 최소 경로를 사용한다.

## 9. GitHub Issue는 언제 쓰나

Execution Mode의 **코드 변경 Task는 GitHub Issue를 기본값**으로 한다.

Issue에 최소:
- Goal
- Why
- Scope
- Out of Scope
- Acceptance Criteria
- Do Not Change
- QA Method

을 둔다.

단순 문서 정리, 작은 조사처럼 코드 변경과 직접 관련이 없는 일은 필요하면 Issue 없이 `templates/TASK.md`만 사용할 수 있다.

GitHub Project Board, Sprint, Story Point 같은 추가 관리 체계는 실제 필요가 생길 때만 도입한다.

## 10. Commit / Test 기록

Execution Mode에서는 **하나의 의미 있는 work cycle을 하나의 추적 가능한 Commit으로 남기는 것**을 기본값으로 한다.

- 채팅 한 번마다 Commit하지 않는다.
- 사소한 저장마다 Commit하지 않는다.
- 하나의 목적을 가진 검토·테스트 가능한 변경 단위로 Commit한다.
- Commit 또는 PR에서 관련 Task / Issue를 찾을 수 있게 한다.
- 작업 결과에는 Result / Tests / Commit / Risk / Not Verified를 남긴다.

예:

```text
feat(#14): add bookmark deletion
```

PR은 모든 작은 변경에 강제하지 않는다. 협업, 리뷰, 위험도가 높은 변경에서 사용한다.

## 11. 새 대화 시작 문장 예시

### Product / PM
```text
GitHub의 최신 PROJECT_INSTRUCTIONS, PROJECT_BRIEF, CURRENT를 기준으로 작업해줘.
이번 역할은 Product / PM이다.
현재 Mode와 기존 Decision을 먼저 확인하고 제품 의미를 임의로 바꾸지 마.
```

### Design
```text
GitHub의 최신 Product Brief, Product Policy, Design System을 기준으로 작업해줘.
이번 역할은 Design이다.
기능 의미는 임의로 바꾸지 말고 필요한 제품 결정은 DECISION NEEDED로 분리해줘.
```

### Development
```text
GitHub의 최신 Tech Stack, Architecture, Engineering Harness와 현재 Task / Issue를 기준으로 작업해줘.
현재 Scope만 구현하고 Test / Commit evidence를 남겨줘.
```

### QA
```text
생성자의 설명을 그대로 믿지 말고 독립 QA 역할로 검수해줘.
Acceptance Criteria, 실제 Evidence, 회귀 위험, 미검증 항목을 확인해 PASS / FIX / DECISION NEEDED로 판정해줘.
```

## 12. 매 작업 후 확인

- 새로운 제품 결정이 생겼는가?
- 정책이 바뀌었는가?
- 기술 선택이 바뀌었는가?
- 현재 상태가 바뀌었는가?
- 다음 Role에 넘길 내용이 있는가?
- 구현 Task라면 Commit / Test / QA Evidence가 남았는가?

있다면 대화에만 남기지 말고 적절한 Canonical Source에 반영한다.

## 13. 파일을 너무 많이 만들지 않는다

작은 프로젝트라면 아래 정도로 합쳐도 된다.

```text
PROJECT_INSTRUCTIONS.md
PROJECT_BOOTSTRAP.md
PROJECT_BRIEF.md
TECH_AND_ARCHITECTURE.md
DESIGN_SYSTEM.md
CURRENT.md
DECISIONS.md
```

프로젝트가 복잡해질 때 역할별 문서와 Harness를 분리한다.

## 14. 최종 목표

Project Folder의 목적은 AI에게 정보를 많이 먹이는 것이 아니다.

**도구와 대화가 바뀌어도 같은 제품을 만들고, 무엇을 왜 바꿨는지 다시 추적할 수 있게 하는 것**이 목표다.
