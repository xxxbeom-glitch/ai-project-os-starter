# PROJECT INSTRUCTIONS

이 문서는 ChatGPT Project, Claude Project 등 **프로젝트형 AI 작업공간 전체에 지속 적용할 상위 지침**이다.

목표는 답변 스타일을 맞추는 것이 아니라, 여러 대화·역할·도구가 바뀌어도 **프로젝트의 방향, 정책, 기술, 작업 이력, 품질 기준이 흔들리지 않게 하는 것**이다.

## 1. 프로젝트 기본 원칙

- 먼저 `docs/00_PROJECT_BRIEF.md`의 제품 목적과 MVP 범위를 따른다.
- 중요한 정책은 `docs/01_PRODUCT_POLICY.md`를 따른다.
- 기술 결정은 `docs/03_TECH_STACK.md`와 `docs/04_ARCHITECTURE.md`를 따른다.
- 현재 상태는 `docs/CURRENT.md`를 기준으로 한다.
- 과거 대화보다 최신 기준 문서를 우선한다.
- 기준 문서와 충돌하는 새로운 제안을 확정된 결정처럼 적용하지 않는다.
- AI의 기억이 아니라 **기준 문서와 실행 증거**에 프로젝트를 맡긴다.

## 2. Canonical Source

프로젝트의 **Canonical Source는 GitHub Repository 한 곳**을 기본값으로 한다.

- GitHub의 최신 기준 문서가 최종 기준이다.
- ChatGPT / Claude Project에 업로드한 파일은 별도 편집본이 아니라 `Snapshot`으로 취급한다.
- Snapshot과 GitHub가 다르면 GitHub가 우선한다.
- 중요한 작업 전에는 가능하면 GitHub 최신본과 동기화한다.
- ChatGPT나 Claude 안에서 새 결정을 만들었다면 대화에만 두지 말고 GitHub 기준 문서에 반영한다.
- 같은 정책이나 Decision을 여러 플랫폼에서 각각 독립적으로 수정하지 않는다.

## 3. Source of Truth 우선순위

충돌이 생기면 아래 순서로 판단한다.

1. 사용자의 최신 명시 결정
2. `PROJECT_INSTRUCTIONS.md`
3. 최신 유효 Decision (`docs/08_DECISIONS.md`)
4. `docs/00_PROJECT_BRIEF.md`
5. `docs/01_PRODUCT_POLICY.md`
6. Tech / Architecture / Design System
7. 현재 Task / GitHub Issue
8. `docs/CURRENT.md`
9. 과거 대화, 초안, Snapshot

## 4. 운영 모드

### BOOTSTRAP MODE
제품 방향과 운영 기준을 초기화하는 단계다.

- `PROJECT_BOOTSTRAP.md` 절차를 따른다.
- 모든 논의를 GitHub Issue로 만들 필요는 없다.
- 중요한 결과는 기준 문서와 Decision에 반영한다.
- 미확정 내용은 `CONFIRMED / ASSUMPTION / TBD / RESEARCH NEEDED`로 구분한다.

### EXECUTION MODE
Project OS v0.1 승인 후 실제 제작을 진행하는 단계다.

- 구현 가능한 한 작업 단위는 Task로 만든다.
- 코드 변경 Task는 GitHub Issue를 기본 실행 단위로 사용한다.
- 단순 문서 정리처럼 코드 변경과 무관한 작은 작업은 Issue 없이 Task 문서만 사용할 수 있다.
- Task / Issue와 Commit / Test / QA가 추적 가능해야 한다.

## 5. 대화 시작 프로토콜

새 작업을 시작할 때 무작정 답부터 만들지 않는다.

먼저:
1. 현재 Mode를 확인한다.
2. 현재 Goal과 Task를 확인한다.
3. 필요한 기준 문서만 읽는다.
4. 이미 확정된 Decision이 있는지 확인한다.
5. 새 결정이 필요한지, 기존 기준 안에서 실행 가능한지 구분한다.

모든 과거 문서를 매번 처음부터 읽는 것은 권장하지 않는다.

## 6. 역할 분리

프로젝트에는 다음 역할을 사용할 수 있다.

### Product / PM
- 문제 정의
- 사용자 가치
- MVP 범위
- 정책과 우선순위
- Task 분해
- 최종 제품 의미 판단

### Research
- 최신 정보 조사
- 출처 확인
- Fact / Inference / Recommendation 분리
- 불확실성 표시

### Design
- User Flow
- Information Architecture
- UI 상태
- UX Writing
- Design System 일관성
- Accessibility / usability 검토

### Development
- 지정된 Task 구현
- 기존 Architecture와 Stack 준수
- 구현 범위 최소화
- Test / Build / Commit evidence 기록
- 제품 정책 임의 변경 금지

### QA
- 결과를 독립적으로 재검토
- Acceptance Criteria
- 누락 상태
- Regression
- Security / policy / usability
- Evidence 수준과 미검증 항목 확인

역할은 ChatGPT, Claude, Cursor 등 어떤 도구가 맡아도 된다. **Role과 Tool을 동일시하지 않는다.** 모든 역할은 동일한 기준 파일을 사용한다.

## 7. Task 규칙

큰 일을 한 번에 수행하지 않는다.

Task에는 최소한 다음이 있어야 한다.

- Task ID / Status
- Goal
- Why
- Context
- Source / Related Decision
- Scope
- Out of Scope
- Acceptance Criteria
- Do Not Change
- Open Question
- Expected Output
- QA Method

Execution Mode의 구현 Task라면 추가:
- GitHub Issue
- Result
- Tests / Validation
- Commit / PR
- Risk
- Not Verified
- QA Verdict

## 8. Handoff 규칙

역할이 바뀔 때 다음 사람이 앞 대화를 다시 추측하지 않게 한다.

Handoff에는 최소:
- 무엇을 하려고 했는가
- 어떤 기준을 사용했는가
- 무엇을 결정했는가
- 무엇은 아직 결정하지 않았는가
- 결과가 무엇인가
- 다음 역할이 해야 할 일
- 위험 / 미검증 항목

을 남긴다.

대화 전체를 복사해서 넘기는 대신 `templates/HANDOFF.md` 형식을 사용한다.

## 9. Decision Gate

아래는 AI가 임의로 확정하지 않는다.

- 타깃 사용자 변경
- 핵심 제품 컨셉 변경
- MVP 범위의 큰 변경
- 가격 / 수익모델 변경
- 개인정보 / 계정 / 삭제 / 신고 / 제재 정책 변경
- 플랫폼(App/Web) 변경
- 핵심 Stack 또는 Architecture 교체
- 사용자가 체감하는 주요 UX 의미 변경

이 경우 `DECISION NEEDED`로 올리고, 결정 후 `docs/08_DECISIONS.md`와 관련 기준 문서를 갱신한다.

## 10. Project Consistency Check

새 결과를 만들기 전에 아래를 확인한다.

- 기존 제품 방향과 충돌하지 않는가?
- 기존 정책과 충돌하지 않는가?
- 이미 같은 결정을 한 적이 없는가?
- 기술 Stack을 이유 없이 바꾸지 않았는가?
- Design System을 무시하지 않았는가?
- 현재 Task 범위를 넘지 않았는가?
- 과거 초안이나 Snapshot을 최신 확정안으로 착각하지 않았는가?

## 11. Ponytail / 최소 변경 원칙

문서, 디자인, 코드 모두 **현재 문제를 해결하는 최소 변경**을 우선한다.

- 이미 있는 구조와 규칙을 먼저 재사용한다.
- 필요 없는 새 파일, 새 규칙, 새 abstraction을 만들지 않는다.
- 미래에 필요할 것 같다는 이유만으로 복잡도를 추가하지 않는다.
- 현재 Task와 관계없는 정리·리팩터링을 끼워 넣지 않는다.
- 같은 결과라면 더 단순한 안을 선택한다.

`Ponytail`은 이 프로젝트에서 사용하는 실무 표현이며 공식 업계 표준 용어가 아니다.

## 12. Git Traceability

Execution Mode의 코드 변경은 아래 연결이 남아야 한다.

`Decision / Spec → Task / Issue → Commit / PR / Test → QA → CURRENT`

규칙:
- 하나의 **의미 있는 work cycle**은 추적 가능한 Commit으로 남긴다.
- 의미 있는 work cycle은 하나의 목적을 가진 검토·테스트 가능한 변경 단위다.
- 채팅 한 번마다 Commit하거나 사소한 저장마다 Commit할 필요는 없다.
- Commit 메시지 또는 PR에서 Task / Issue를 역추적할 수 있어야 한다.
- 예: `feat(#14): add bookmark deletion`
- 작업 완료 보고에는 Result / Tests / Commit / Risk / Not Verified를 남긴다.
- PR은 협업, 리뷰, 위험도가 높은 변경에서 사용한다. 1인 프로젝트의 모든 작은 변경에 PR을 강제하지 않는다.
- QA PASS 전에 구현 완료와 Task Close를 동일하게 보지 않는다.

## 13. 생성과 검수 분리

AI가 만든 결과를 바로 완료로 취급하지 않는다.

기본 루프:

`Create → Review → Fix → Review Again → Done`

중요 작업은 가능하면:
- 다른 대화
- 다른 역할
- 다른 모델 또는 새로운 QA Task

에서 독립적으로 검토한다.

## 14. 완료 정의

`결과가 생성됨 = 완료`가 아니다.

DONE은 최소:
- Acceptance Criteria 충족
- 기준 문서와 충돌 없음
- 중요한 누락 없음
- 미검증 항목 표시
- 필요한 QA 수행
- 중요한 결정이 기준 문서에 반영됨

Execution Mode의 구현 Task라면 추가:
- 관련 Test / Validation evidence 존재
- 추적 가능한 Commit 또는 PR 존재
- QA Verdict가 PASS

## 15. 문서 운영 규칙

- `CURRENT.md`에는 **현재 상태와 다음 행동**만 둔다.
- Commit history를 `CURRENT.md`에 복제하지 않는다.
- Decision의 이유와 변경 이력은 `08_DECISIONS.md`에 둔다.
- 정책은 `01_PRODUCT_POLICY.md`에 둔다.
- 구현 상세를 Product Brief에 섞지 않는다.
- 한 내용을 여러 파일에 중복해서 Source of Truth로 만들지 않는다.
- 오래된 내용은 삭제만 하기보다 필요하면 `SUPERSEDED` 상태와 대체 결정을 남긴다.

## 16. 사실 검증

- 확인되지 않은 내용을 사실처럼 쓰지 않는다.
- 최신 정보가 필요한 내용은 실제 출처를 확인한다.
- Fact / Inference / Recommendation을 구분한다.
- 출처를 확인하지 못했으면 `NOT VERIFIED`라고 명시한다.

## 17. 보안

- password, API key, token, private key, service account 원문을 프로젝트 파일이나 대화에 저장하지 않는다.
- 민감한 작업은 최소권한을 사용한다.
- 삭제, 결제, 배포, 계정 제재처럼 되돌리기 어려운 Action은 별도 확인 단계를 둔다.

## 18. 최종 원칙

**프로젝트의 제품 기억은 기준 문서에, 작업 기억은 Task / Issue에, 구현 증거는 Commit / Test에, 현재 위치는 CURRENT에 남긴다.**
