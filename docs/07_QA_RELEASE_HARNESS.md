# 07 QA & RELEASE HARNESS

## 목적
AI가 “완료했습니다”라고 말하는 것과 실제 제품이 완료된 것을 분리한다.

QA는 생성자의 설명이 아니라 **Acceptance Criteria와 실제 Evidence**를 기준으로 판정한다.

## 1. Evidence Level

- `E0 — CLAIM ONLY`: 생성자 또는 작업자의 주장만 있음
- `E1 — DOC REVIEW`: 요구사항, 정책, 설계, 문서 수준 검토
- `E2 — ARTIFACT REVIEW`: 코드, diff, 화면, 산출물을 직접 확인
- `E3 — TEST VERIFIED`: 관련 자동 테스트 / build / lint 등 실행 증거 확인
- `E4 — REAL ENV VERIFIED`: 실제 기기, 실제 환경, 실제 사용자 흐름 수준 검증

모든 Task가 E4를 요구하지는 않는다. 위험도와 Task 특성에 맞는 Evidence 수준을 정한다.

코드 구현 Task를 `E0`만으로 PASS하지 않는다.

## 2. QA Pipeline

```text
Q0 Product / Spec
→ Q1 Functional
→ Q2 State / Edge Case
→ Q3 Data / Security
→ Q4 UX / Accessibility
→ Q5 Regression
→ Q6 Release
```

작업 성격에 따라 필요 없는 단계는 `N/A`로 표시할 수 있다. 중요한 것은 형식적 단계 수가 아니라 필요한 위험을 실제로 검증하는 것이다.

## Q0 Product / Spec
- Acceptance Criteria 충족?
- Product Policy와 충돌 없음?
- MVP Scope 안인가?
- 임의 요구사항 추가 / 삭제 없음?
- Decision Needed를 구현 편의로 우회하지 않았는가?

## Q1 Functional
- 정상 흐름 동작
- 저장 / 수정 / 삭제 실제 반영
- 로그인 / 로그아웃
- 권한 없는 접근 차단
- 실패 후 복구 가능

## Q2 State / Edge Case
필요한 범위에서 확인:
- Default
- Loading
- Empty
- Error
- Success
- Disabled
- Retry
- 긴 텍스트
- 느린 네트워크
- 중복 클릭
- 중복 요청 / 재시도

## Q3 Data / Security
- 사용자 A가 사용자 B 데이터에 접근할 수 없는가
- 서버 ownership / RLS 등 실제 권한 경계가 적용되는가
- 인증 없는 mutation이 차단되는가
- secret이 client / repo / log에 노출되지 않는가
- 데이터 삭제 / 보관 정책과 실제 동작이 충돌하지 않는가

## Q4 UX / Accessibility
- 사용자의 다음 행동이 명확한가
- 오류 후 복구할 수 있는가
- keyboard navigation 가능 여부
- form label
- focus state
- color contrast
- 좁은 viewport
- 주요 상태에서 UX 의미가 일관적인가

## Q5 Regression
공용 component, shared logic, data layer, auth, payment 등 공통 영역을 수정했다면 영향을 받는 기존 흐름을 다시 확인한다.

Regression 범위를 확인하지 못했다면 `NOT VERIFIED`로 남긴다.

## Q6 Release Gate
Release 후보의 일반 기준:
- P0 blocker 0
- 핵심 사용자 흐름 검증
- 필요한 test / typecheck / lint / build PASS
- production env 확인
- debug / fake data 제거
- secret 노출 여부 확인
- rollback 또는 빠른 수정 경로 확인
- Release에 필요한 실제 환경 검증 수행

실제 프로젝트에 필요한 Release Gate는 제품 위험도에 맞게 조정한다.

## 3. PASS / FIX / DECISION NEEDED

### PASS
Acceptance Criteria와 해당 Task에 필요한 Evidence 수준을 충족했다.

### FIX
현재 기준 안에서 수정 가능한 명확한 결함이 있다.

### DECISION NEEDED
제품 의미, 정책, Scope 선택이 필요해 QA가 임의로 정답을 만들면 안 된다.

`NOT VERIFIED`를 `PASS`로 간주하지 않는다.

## 4. Severity

- `P0`: 출시 또는 핵심 기능을 막는 blocker
- `P1`: 중요한 기능 / 정책 / 데이터 / UX 결함
- `P2`: 경미한 결함 또는 개선 항목

취향 차이나 비필수 개선을 P0/P1로 과장하지 않는다.

## 5. QA Agent 규칙

- 가능하면 결과를 만든 Role과 다른 관점에서 검수한다.
- 같은 대화에서 검토하더라도 Acceptance Criteria부터 다시 읽고 결과를 역으로 대조한다.
- Development의 완료 보고만 읽고 PASS하지 않는다.
- 코드 Task라면 관련 Commit / PR / diff / Test evidence를 확인한다.
- 필요한 경우 실제 화면 / 실제 기기 / 실제 환경 검증을 별도 단계로 둔다.

## 6. QA 완료 기록

QA 결과에는 최소 다음이 남아야 한다.

```text
QA Target:
Verdict:
Evidence Level:
Evidence:
Findings:
Regression Risk:
Not Verified:
Required Fix:
Next Role:
```

Execution Mode에서는 QA PASS가 Task / Issue Close의 근거가 된다.
