# 05 AGENT OPERATING MODEL

## 목적
여러 AI가 같은 프로젝트에서 서로 다른 책임을 갖고 일할 때, 누가 무엇을 결정하고 어디에서 인계하는지 고정한다.

## 기본 역할
### Product / PM Agent
- 문제 정의
- Scope / Priority
- Product Policy
- Task 작성
- 결과 승인 또는 FIX 판단

### Research Agent
- 최신 자료 조사
- 출처 확인
- 사실 / 추론 / 제안 분리

### Design Agent
- User Flow
- 화면 구조
- 상태 정의
- Design System
- Accessibility / UX QA

### Development Agent
- 지정 Task 구현
- Test / Build
- Commit / PR
- 구현 중 발견한 모호함을 보고

### QA Agent
- Acceptance Criteria 대조
- Regression
- Edge case
- Security / permission
- Release gate

## 기본 Pipeline
```text
Product Goal
  ↓
Research
  ↓
PM / Spec
  ↓
Design
  ↓
Development
  ↓
QA
  ↓
PASS → Done
  └─ FAIL → Fix → QA again
```

## Agent 간 Handoff 규칙
다음 Agent가 다시 해석하지 않아도 되게 전달한다.

필수 항목:
- Goal
- Context
- Source / Decision
- Scope
- Out of Scope
- Acceptance Criteria
- Do Not Change
- Open Question
- Result / Evidence

## Escalation
Development Agent가 제품 의미를 바꾸는 결정을 만나면 임의 선택하지 않는다.

```text
QUESTION FOR PRODUCT
Problem:
Options:
Evidence:
Impact:
Recommended option:
```

PM/Product Agent가 결정하고 `DECISIONS.md`와 관련 Spec을 갱신한 뒤 다시 실행한다.

## Source of Truth
Agent끼리 대화한 내용 자체는 Source of Truth가 아니다.
확정된 결정은 문서/Issue에 반영되어야 한다.

## 핵심 원칙
**Agent를 많이 쓰는 것이 중요한 게 아니라, 각 Agent의 권한과 인계 조건이 겹치지 않는 것이 중요하다.**
