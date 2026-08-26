# 05 AGENT OPERATING MODEL

## 목적
같은 ChatGPT/Claude Project 안에서 여러 대화나 역할을 나눠 사용하더라도 **하나의 제품 방향과 기준을 유지하기 위한 협업 구조**를 정의한다.

여기서 Agent는 꼭 완전 자동화된 프로그램을 뜻하지 않는다.

`PM 역할 대화`, `Research 역할 대화`, `Design 역할 대화`, `Development 역할 대화`, `QA 역할 대화`처럼 **같은 AI를 역할별로 나눠 쓰는 방식도 포함**한다.

## 가장 중요한 전제

각 대화가 서로의 최신 내용을 자동으로 모두 기억한다고 가정하지 않는다.

따라서:
- 대화 = 작업 공간
- `docs/` = 프로젝트 기준
- `CURRENT.md` = 현재 위치
- `HANDOFF` = 역할 사이의 전달 문서

로 구분한다.

## 기본 역할

### Product / PM
제품 의미와 우선순위를 소유한다.
- 문제 정의
- 사용자 가치
- MVP / Non-goal
- Policy
- Business 조건
- Task 분해
- 제품 질문 결정 또는 사용자에게 escalation

### Research
결정에 필요한 근거를 제공한다.
- 최신 자료 조사
- 출처 확인
- 사실 / 추론 / 제안 분리
- 불확실성 표시

### Design
제품 요구를 사용 가능한 경험으로 구체화한다.
- User Flow
- IA
- UI State
- UX Writing
- Design System
- Accessibility / Usability
- Development Handoff

### Development
확정된 기준을 구현 가능한 구조와 결과로 옮긴다.
- 기존 Stack / Architecture 준수
- 지정 Task 범위 실행
- Test / validation
- 구현 제약과 기술 Blocker 보고
- 제품 정책 임의 변경 금지

### QA
생성 역할과 독립된 관점으로 검수한다.
- Acceptance Criteria
- 누락
- Regression
- Edge case
- Security / Policy
- 미검증 항목
- PASS / FIX / DECISION NEEDED

## 기본 Pipeline

```text
Product Goal
   ↓
Product / PM — Task와 기준 정의
   ↓
Research — 필요한 근거
   ↓
Design — UX/UI 명세
   ↓
Development — 구현/기술 결과
   ↓
QA — 독립 검수
   ├─ PASS → 기준 문서/CURRENT 갱신
   ├─ FIX → 해당 역할로 반환
   └─ DECISION NEEDED → Product/User 판단 → 관련 문서 갱신
```

모든 Task가 모든 Role을 거칠 필요는 없다.

예:
- 시장 조사: PM → Research → PM
- UI 문구 수정: Design → QA
- 기술 버그: Development → QA
- 새 결제 기능: PM → Research → Design → Development → QA

## Role 시작 규칙

역할을 시작할 때 다음 네 가지를 먼저 확인한다.

1. 이번 Role은 무엇인가?
2. 현재 Task는 무엇인가?
3. 어떤 기준 문서를 읽어야 하는가?
4. 이 Role이 결정해도 되는 것과 결정하면 안 되는 것은 무엇인가?

`roles/` 폴더의 역할 파일을 사용한다.

## Handoff 규칙

역할 변경 시 이전 대화 전체를 던지지 않는다.

`templates/HANDOFF.md`를 기준으로 다음만 압축해서 전달한다.

- Goal
- Context
- Source of Truth Used
- Confirmed
- Not Decided
- Result
- Do Not Change
- Evidence
- Risk / Not Verified
- Next Action

핵심은 **다음 역할이 다시 처음부터 추론하지 않게 하는 것**이다.

## 예시: Design → Development

```text
Goal:
북마크 저장 Form을 구현 가능한 수준으로 정의

Confirmed:
- URL 필수
- 제목은 자동 추출 가능하지만 사용자가 수정 가능
- 카테고리는 선택 사항

Do Not Change:
- 회원가입 방식
- 무료 사용자 저장 개수 정책

Result:
- Save Form field/state/copy 정의 완료
- Loading/Error/Success 포함

Next:
Development가 현재 Stack 안에서 구현
```

## 예시: Development → QA

```text
Task:
TSK-004 Bookmark Save

Result:
저장/중복/오류 처리 구현

Evidence:
테스트 결과와 확인한 범위

Not Verified:
모바일 Safari 실기기 미확인

Next:
QA가 AC/Regression/State 검수
```

## DECISION NEEDED

Role의 권한 밖에서 제품 의미가 달라지는 선택이 필요하면 임의로 확정하지 않는다.

```text
DECISION NEEDED
Question:
Options:
Evidence:
Impact:
Recommendation:
```

Product / PM 또는 사용자가 결정한 뒤:
1. `docs/08_DECISIONS.md` 기록
2. 관련 Policy / Tech / Design 문서 갱신
3. Task 재개

## 문서 갱신 소유권

Role이 대화 안에서 결론을 냈다고 끝이 아니다.

- 새 제품 방향 → Project Brief / Decision
- 새 정책 → Product Policy / Decision
- 기술 기준 → Tech Stack / Architecture / Decision
- 디자인 기준 → Design System / Decision
- 현재 진행 상태 → CURRENT

에 반영해야 다음 대화에서도 같은 기준을 사용할 수 있다.

## Anti-Drift 규칙

여러 대화를 오래 사용하다 보면 프로젝트가 조금씩 달라지는 현상을 `drift`라고 본다.

방지 방법:
- 중요한 결론은 파일에 반영
- 과거 대화보다 최신 기준 파일 우선
- Role마다 권한 제한
- Handoff에 `Do Not Change` 포함
- QA에서 Policy / Decision 충돌 확인
- CURRENT는 짧고 최신으로 유지

## 핵심 원칙

**AI 역할끼리 실제로 대화를 많이 하는 것보다, 모두가 같은 기준 파일을 읽고 표준 Handoff를 남기는 것이 더 중요하다.**
