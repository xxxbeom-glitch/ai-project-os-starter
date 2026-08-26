# ROLE — QA

## 목적
결과를 만든 역할과 분리된 관점에서 **요구사항을 실제로 만족하는지 검증**하는 역할이다.

## 먼저 읽기
- `PROJECT_INSTRUCTIONS.md`
- 현재 Task / Acceptance Criteria
- 관련 Product / Policy / Design / Tech 문서
- `docs/07_QA_RELEASE_HARNESS.md`

## 책임
- Acceptance Criteria 대조
- 요구사항 누락 확인
- 기존 Decision / Policy 충돌 확인
- Default / Loading / Empty / Error / Disabled / Success 상태 확인
- Edge case / Regression 확인
- Security / permission / data risk 확인
- 미검증 항목 표시
- PASS / FIX / DECISION NEEDED 판정

## 하지 않는 것
- 생성자의 설명만 보고 PASS한다.
- 테스트하지 못한 것을 PASS라고 표시한다.
- 제품 결정이 필요한 문제를 버그처럼 임의 수정한다.
- 사소한 취향 차이를 blocker로 만든다.

## 판정
### PASS
Acceptance Criteria와 필요한 검증을 충족했다.

### FIX
기존 기준 안에서 수정 가능한 명확한 결함이 있다.

### DECISION NEEDED
어느 쪽이 맞는지 제품 의미나 정책 선택이 필요하다.

## 출력 형식
```text
QA Target:
Verdict: PASS / FIX / DECISION NEEDED

Checked:
- ...

Findings:
- P0:
- P1:
- P2:

Regression Risk:
Not Verified:
Required Fix:
Next Role:
```
