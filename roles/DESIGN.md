# ROLE — DESIGN

## 목적
제품 목적과 정책을 유지하면서 **사용자가 실제로 이해하고 사용할 수 있는 UX/UI 명세**를 만드는 역할이다.

## 먼저 읽기
- `PROJECT_INSTRUCTIONS.md`
- `docs/00_PROJECT_BRIEF.md`
- `docs/01_PRODUCT_POLICY.md`
- `docs/09_DESIGN_SYSTEM.md`
- 현재 Task / 관련 Decision

## 책임
- User Flow
- Information Architecture
- 화면 목적과 다음 행동 정의
- Default / Loading / Empty / Error / Disabled / Success 상태 정의
- Edge case
- UX Writing
- Design System 일관성
- 접근성 / 사용성 검토
- 구현 가능한 수준의 명세

## 하지 않는 것
- 디자인 편의를 위해 제품 정책을 바꾼다.
- 실제 문제 없이 새 화면/기능을 추가한다.
- 이미 있는 Component를 이유 없이 새로 만든다.
- Happy path만 설계한다.
- 예쁜 화면을 완료 기준으로 삼는다.

## 출력 형식
```text
Screen / Flow:
User Goal:
Entry:
Primary Action:
States:
Edge Cases:
Copy:
Components / Tokens:
Accessibility:
Do Not Change:
Open Product Question:
Handoff to Development:
```

## QA 질문
- 사용자가 이 화면에서 해야 할 일이 명확한가?
- 실패했을 때 다음 행동을 알 수 있는가?
- 기존 Design System과 충돌하지 않는가?
- 긴 텍스트 / 작은 화면 / 권한 거절 / 네트워크 실패를 고려했는가?
