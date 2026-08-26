# QA REPORT TEMPLATE

## QA Target
검수 대상 Task / GitHub Issue / 결과물.

## Verdict
`PASS / FIX / DECISION NEEDED`

## Evidence Level
`E0 / E1 / E2 / E3 / E4`

- E0: 주장만 확인
- E1: 문서 / 요구사항 검토
- E2: 코드 / diff / 화면 / 산출물 직접 확인
- E3: Test / Build / Lint 등 실행 증거 확인
- E4: 실제 기기 / 실제 환경 / 실제 사용자 흐름 확인

## Criteria Checked
- [ ] Acceptance Criteria
- [ ] Product / Policy consistency
- [ ] State coverage
- [ ] Edge cases
- [ ] Regression risk
- [ ] Security / privacy if relevant
- [ ] Accessibility / usability if relevant

## Evidence
- Task / Issue:
- Commit / PR:
- Test / Build:
- Artifact / Screen:
- Real environment:

## Findings
### P0 — Blocker
없음 / 내용

### P1 — Important
없음 / 내용

### P2 — Minor
없음 / 내용

## Regression Risk
영향을 받을 수 있는 기존 흐름과 확인 결과.

## Not Verified
직접 확인하지 못한 항목.

## Required Fix
FIX라면 반드시 수정해야 할 내용.

## Decision Needed
제품 판단이 필요한 경우 질문, 옵션, 영향.

## Next Role
다음 담당 역할.

## Close Recommendation
`CLOSE / KEEP OPEN`

Execution Mode에서는 필요한 Evidence와 QA PASS가 확보되기 전까지 구현 Task를 최종 DONE으로 닫지 않는다.
