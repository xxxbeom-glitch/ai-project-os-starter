# 07 QA & RELEASE HARNESS

## 목적
AI가 “완료했습니다”라고 말하는 것과 실제 제품이 완료된 것을 분리한다.

## QA Pipeline
```text
Q0 Product / Spec
→ Q1 Functional
→ Q2 State / Edge Case
→ Q3 Data / Security
→ Q4 UX / Accessibility
→ Q5 Regression
→ Q6 Release
```

## Q0 Product / Spec
- Acceptance Criteria 충족?
- Product Policy와 충돌 없음?
- MVP Scope 안인가?
- 임의 요구사항 추가/삭제 없음?

## Q1 Functional
- 정상 흐름 동작
- 저장/수정/삭제 실제 반영
- 로그인/로그아웃
- 권한 없는 접근 차단

## Q2 State / Edge Case
최소 확인:
- Loading
- Empty
- Error
- Success
- Disabled
- Retry
- 긴 텍스트
- 느린 네트워크
- 중복 클릭

## Q3 Data / Security
- 사용자 A가 사용자 B 데이터에 접근할 수 없는가
- 서버 ownership/RLS가 적용되는가
- 인증 없는 mutation이 차단되는가
- secret이 client/repo/log에 노출되지 않는가

## Q4 UX / Accessibility
- 사용자의 다음 행동이 명확한가
- 오류 후 복구할 수 있는가
- keyboard navigation 가능 여부
- form label
- focus state
- color contrast
- 좁은 viewport

## Q5 Regression
공용 component나 data layer를 수정했다면 사용하는 기존 흐름도 다시 확인한다.

## Q6 Release Gate
Release 후보 조건:
- P0 blocker 0
- 핵심 E2E PASS
- test/typecheck/lint/build PASS
- production env 확인
- debug/fake data 제거
- secret scan
- rollback 또는 빠른 수정 경로 확인

## PASS / FAIL 표기
- `PASS`: 직접 확인 근거 있음
- `FAIL`: 기준 불충족
- `NOT VERIFIED`: 아직 확인하지 못함

`NOT VERIFIED`를 `PASS`로 간주하지 않는다.

## QA Agent 규칙
가능하면 결과를 만든 Agent와 다른 관점에서 검수한다.
같은 대화에서 검토하더라도 Acceptance Criteria부터 다시 읽고 결과를 역으로 대조한다.
