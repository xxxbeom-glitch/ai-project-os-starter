# AI PROJECT BOOTSTRAP

이 문서는 이 Starter를 새 프로젝트로 복사한 직후, **LLM이 사용자를 인터뷰하고 프로젝트의 초기 기준을 확정하는 절차**를 정의한다.

목표는 미래를 전부 설계하는 것이 아니다. 실제 기획·디자인·개발을 시작해도 프로젝트가 쉽게 흔들리지 않을 정도의 **최소 Project OS v0.1**을 만드는 것이다.

## 1. 두 가지 운영 모드

### BOOTSTRAP MODE
아직 제품의 핵심 기준을 정하는 단계다.

주요 산출물:
- Product Brief
- Product Policy
- Business Model
- Tech Stack
- Architecture의 최소 기준
- Design 방향
- Agent / Role 운영 방식
- Engineering / QA Harness
- Decisions

이 단계에서는 GitHub Issue를 모든 논의마다 만들 필요가 없다. 중요한 것은 **결정과 근거를 기준 문서에 남기는 것**이다.

### EXECUTION MODE
Project OS v0.1이 승인된 뒤 실제 제작을 진행하는 단계다.

기본 흐름:

`Decision / Spec → Task or GitHub Issue → Implementation → Commit / Test Evidence → Independent QA → Close → CURRENT update`

실제 구현 Task는 GitHub Issue를 기본 실행 단위로 사용한다. 단순 문서 정리처럼 코드 변경과 무관한 작은 작업은 Issue 없이 Task 문서만 사용할 수 있다.

## 2. 결정 상태

Bootstrap 중 모든 항목을 억지로 확정하지 않는다. 아래 상태를 사용한다.

- `CONFIRMED` — 사용자 승인 또는 충분한 근거로 현재 확정
- `ASSUMPTION` — 검증 전 임시 가설
- `TBD` — 아직 결정할 필요가 없음
- `RESEARCH NEEDED` — 외부 조사나 추가 근거가 필요

LLM은 빈칸을 그럴듯하게 추측해서 `CONFIRMED`로 만들지 않는다.

## 3. Bootstrap 시작 프로토콜

Starter를 새 Repository로 복사한 뒤 LLM은 먼저 다음을 수행한다.

1. `README.md`를 읽어 구조와 목적을 이해한다.
2. `PROJECT_INSTRUCTIONS.md`를 읽어 상위 규칙을 확인한다.
3. `PROJECT_BOOTSTRAP.md`를 읽어 Bootstrap 절차를 따른다.
4. `docs/`의 예시 내용을 실제 사용자 결정으로 간주하지 않는다.
5. 현재 프로젝트에 맞게 다시 결정해야 할 항목을 추출한다.
6. 질문을 한 번에 과도하게 던지지 않고 단계별 인터뷰를 시작한다.

## 4. 인터뷰 순서

### Phase 1 — Product
확인할 것:
- 무엇을 만드는가
- 왜 필요한가
- 누구를 위한 것인가
- 사용자의 핵심 문제는 무엇인가
- 핵심 가치 제안은 무엇인가
- MVP에 반드시 포함할 것은 무엇인가
- 하지 않을 것은 무엇인가

주요 반영 파일:
- `docs/00_PROJECT_BRIEF.md`

### Phase 2 — Policy / Business
확인할 것:
- 계정 / 인증 정책
- 개인정보 / 데이터 보관 / 삭제
- 콘텐츠 / 신고 / 제재가 필요한가
- 결제 또는 수익모델이 있는가
- 핵심 비용은 무엇인가
- 무엇을 사업 가설로 검증할 것인가

주요 반영 파일:
- `docs/01_PRODUCT_POLICY.md`
- `docs/02_BUSINESS_MODEL.md`

### Phase 3 — Platform / Technology
확인할 것:
- Web / App / Both
- 플랫폼 우선순위
- 언어 / Framework
- Backend / Database
- Auth
- 배포
- 외부 서비스
- 보안 또는 정책상 제약

LLM은 단순 취향이 아니라 제품 제약, 비용, 개발 속도, 운영 난이도에 근거해 추천한다.

주요 반영 파일:
- `docs/03_TECH_STACK.md`
- `docs/04_ARCHITECTURE.md`

### Phase 4 — UX / Design
확인할 것:
- 핵심 사용자 흐름
- 정보구조
- 제품의 시각적 방향
- 디자인 시스템의 최소 기준
- 반드시 고려할 UI 상태
- 접근성 / 사용성 제약

주요 반영 파일:
- `docs/09_DESIGN_SYSTEM.md`

### Phase 5 — Operating Model
확인할 것:
- Product / Research / Design / Development / QA 역할 중 필요한 역할
- 어떤 역할이 어떤 결정을 할 수 있는가
- Handoff 방식
- Decision Gate
- Do / Don't
- Ponytail / 최소 변경 원칙
- QA와 Release 기준

주요 반영 파일:
- `docs/05_AGENT_OPERATING_MODEL.md`
- `docs/06_ENGINEERING_HARNESS.md`
- `docs/07_QA_RELEASE_HARNESS.md`

## 5. 질문 분류

LLM은 인터뷰 중 질문과 제안을 다음 세 종류로 구분한다.

### USER DECISION
사용자의 제품 의도나 사업 의지가 필요한 항목.

예:
- 누구를 타깃으로 할 것인가
- 유료화할 것인가
- 익명 사용을 허용할 것인가

### RESEARCH REQUIRED
외부 사실 확인이 필요한 항목.

예:
- 플랫폼 정책
- 최신 가격
- 법적 / 운영 제약
- 경쟁 서비스 현황

### AI RECOMMENDATION
현재 조건을 바탕으로 LLM이 근거와 trade-off를 제시할 수 있는 항목.

예:
- MVP는 Web이 유리한가 App이 유리한가
- 현재 규모에서 어떤 Stack이 단순한가

추천은 자동 결정이 아니다. Decision Gate에 해당하면 사용자 승인을 받는다.

## 6. 각 Phase 종료 조건

각 Phase가 끝나면 LLM은 다음을 요약한다.

```text
CONFIRMED:
ASSUMPTIONS:
TBD:
RESEARCH NEEDED:
CONFLICTS FOUND:
FILES TO UPDATE:
```

사용자가 중요한 제품 결정을 승인한 뒤 해당 기준 파일에 반영한다.

## 7. Cross-document QA

Bootstrap 종료 전에 전체 기준 문서를 다시 읽고 다음을 교차 검수한다.

- Product Brief와 Policy가 충돌하지 않는가
- Business Model이 제품 경험을 깨뜨리지 않는가
- Tech Stack이 실제 요구보다 과도하지 않은가
- Architecture가 MVP 규모보다 복잡하지 않은가
- Design 기준과 Product 목표가 충돌하지 않는가
- Agent 역할의 권한이 중복되거나 비어 있지 않은가
- Engineering Harness와 QA Harness가 실제로 실행 가능한가
- 같은 결정이 여러 파일에서 서로 다른 내용으로 중복되어 있지 않은가
- `ASSUMPTION / TBD / RESEARCH NEEDED`가 `CONFIRMED`처럼 쓰이지 않았는가

LLM은 발견한 문제를 임의로 숨기거나 조용히 수정하지 않고 사용자에게 보고한다.

## 8. Project OS v0.1 Freeze

아래 조건을 만족하면 Bootstrap을 완료할 수 있다.

- Product 목적과 MVP가 명확하다.
- 중요한 정책이 결정되었거나 상태가 표시되어 있다.
- Platform / Tech 방향이 구현 시작에 충분하다.
- 필요한 Design 기준이 있다.
- Role / Decision Gate / QA 기준이 있다.
- 주요 문서 간 치명적 충돌이 없다.
- `CURRENT.md`에 현재 상태와 다음 Task가 기록되어 있다.

이 시점을 `Project OS v0.1`로 본다.

`Freeze`는 영구 고정이라는 뜻이 아니다. 이후 변경은 새 Decision으로 남기고 관련 기준 문서를 갱신한다.

## 9. Execution Mode 전환

실제 구현이 시작되면 다음 규칙을 적용한다.

- 구현 가능한 한 작업 단위를 Task로 만든다.
- 코드 변경 Task는 GitHub Issue를 기본값으로 사용한다.
- Issue에는 Goal / Scope / Acceptance Criteria / Do Not Change / QA Method가 있어야 한다.
- 하나의 의미 있는 work cycle은 추적 가능한 Commit으로 남긴다.
- Commit 또는 PR에서 Task / Issue를 역추적할 수 있어야 한다.
- 구현 완료 보고에는 Result / Tests / Commit / Risk / Not Verified를 남긴다.
- 독립 QA가 PASS한 뒤 Issue를 닫는다.
- 프로젝트의 현재 위치가 바뀌면 `CURRENT.md`를 갱신한다.

## 10. 최종 원칙

**Bootstrap은 문서를 많이 만드는 과정이 아니라, AI가 프로젝트를 임의로 재해석하지 못하도록 필요한 판단 기준을 먼저 만드는 과정이다.**
