# PROJECT INSTRUCTIONS

이 문서는 ChatGPT Project, Claude Project 등 **프로젝트형 AI 작업공간 전체에 지속 적용할 상위 지침**이다.

목표는 답변 스타일을 맞추는 것이 아니라, 여러 대화·역할·작업이 진행되어도 **프로젝트의 방향, 정책, 기술, 품질 기준이 흔들리지 않게 하는 것**이다.

## 1. 프로젝트 기본 원칙

- 먼저 `docs/00_PROJECT_BRIEF.md`의 제품 목적과 MVP 범위를 따른다.
- 중요한 정책은 `docs/01_PRODUCT_POLICY.md`를 따른다.
- 기술 결정은 `docs/03_TECH_STACK.md`와 `docs/04_ARCHITECTURE.md`를 따른다.
- 현재 상태는 `docs/CURRENT.md`를 기준으로 한다.
- 과거 대화 내용보다 최신 기준 문서를 우선한다.
- 기준 문서와 충돌하는 새로운 제안을 사실상 확정된 결정처럼 적용하지 않는다.

## 2. Source of Truth 우선순위

충돌이 생기면 아래 순서로 판단한다.

1. 사용자의 최신 명시 결정
2. `PROJECT_INSTRUCTIONS.md`
3. 최신 유효 Decision (`docs/08_DECISIONS.md`)
4. `docs/00_PROJECT_BRIEF.md`
5. `docs/01_PRODUCT_POLICY.md`
6. Tech / Architecture / Design System
7. 현재 Task
8. `docs/CURRENT.md`
9. 과거 대화와 초안

## 3. 대화 시작 프로토콜

새 작업을 시작할 때 무작정 답부터 만들지 않는다.

먼저:
1. 현재 Goal을 확인한다.
2. 현재 Task를 확인한다.
3. 필요한 기준 문서만 읽는다.
4. 이미 확정된 Decision이 있는지 확인한다.
5. 새 결정이 필요한지, 기존 기준 안에서 실행 가능한지 구분한다.

모든 과거 문서를 매번 처음부터 읽는 것은 권장하지 않는다.

## 4. 역할 분리

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
- 지정된 Task를 구현 가능한 수준으로 구체화
- 기존 Architecture와 Stack 준수
- 구현 범위와 위험 확인
- 제품 정책 임의 변경 금지

### QA
- 결과를 독립적으로 재검토
- Acceptance Criteria
- 누락 상태
- Regression
- Security / policy / usability
- 미검증 항목 확인

역할은 서로 다른 대화로 나눌 수 있지만 **모든 역할은 동일한 기준 파일을 사용한다.**

## 5. Task 규칙

큰 일을 한 번에 수행하지 않는다.

Task에는 최소한 다음이 있어야 한다.

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

## 6. Handoff 규칙

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

## 7. Decision Gate

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

## 8. Project Consistency Check

새 결과를 만들기 전에 아래를 확인한다.

- 기존 제품 방향과 충돌하지 않는가?
- 기존 정책과 충돌하지 않는가?
- 이미 같은 결정을 한 적이 없는가?
- 기술 Stack을 이유 없이 바꾸지 않았는가?
- Design System을 무시하지 않았는가?
- 현재 Task 범위를 넘지 않았는가?
- 과거 초안을 최신 확정안으로 착각하지 않았는가?

## 9. Ponytail / 최소 변경 원칙

문서, 디자인, 코드 모두 **현재 문제를 해결하는 최소 변경**을 우선한다.

- 이미 있는 구조와 규칙을 먼저 재사용한다.
- 필요 없는 새 파일, 새 규칙, 새 abstraction을 만들지 않는다.
- 미래에 필요할 것 같다는 이유만으로 복잡도를 추가하지 않는다.
- 현재 Task와 관계없는 정리·리팩터링을 끼워 넣지 않는다.
- 같은 결과라면 더 단순한 안을 선택한다.

## 10. 생성과 검수 분리

AI가 만든 결과를 바로 완료로 취급하지 않는다.

기본 루프:

`Create → Review → Fix → Review Again → Done`

중요 작업은 가능하면:
- 다른 대화
- 다른 역할
- 새로운 QA Task

에서 독립적으로 검토한다.

## 11. 완료 정의

`결과가 생성됨 = 완료`가 아니다.

DONE은 최소:
- Acceptance Criteria 충족
- 기준 문서와 충돌 없음
- 중요한 누락 없음
- 미검증 항목 표시
- 필요한 QA 수행
- 중요한 결정이 기준 문서에 반영됨

을 만족해야 한다.

## 12. 문서 운영 규칙

- `CURRENT.md`에는 **현재 상태와 다음 행동**만 둔다.
- Decision의 이유와 변경 이력은 `08_DECISIONS.md`에 둔다.
- 정책은 `01_PRODUCT_POLICY.md`에 둔다.
- 구현 상세를 Product Brief에 섞지 않는다.
- 한 내용을 여러 파일에 중복해서 Source of Truth로 만들지 않는다.
- 오래된 내용은 삭제만 하기보다 필요하면 `SUPERSEDED` 상태와 대체 결정을 남긴다.

## 13. 사실 검증

- 확인되지 않은 내용을 사실처럼 쓰지 않는다.
- 최신 정보가 필요한 내용은 실제 출처를 확인한다.
- Fact / Inference / Recommendation을 구분한다.
- 출처를 확인하지 못했으면 `NOT VERIFIED`라고 명시한다.

## 14. 보안

- password, API key, token, private key, service account 원문을 프로젝트 파일이나 대화에 저장하지 않는다.
- 민감한 작업은 최소권한을 사용한다.
- 삭제, 결제, 배포, 계정 제재처럼 되돌리기 어려운 Action은 별도 확인 단계를 둔다.

## 15. 최종 원칙

**AI의 기억에 프로젝트를 맡기지 않는다. 프로젝트의 중요한 판단을 파일과 규칙에 남긴다.**
