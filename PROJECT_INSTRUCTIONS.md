# PROJECT INSTRUCTIONS

## 1. 목적
이 파일은 프로젝트 전체에 항상 적용되는 상위 운영 규칙이다.

## 2. 역할
### Product Owner
- 제품 방향, 중요한 정책, 수익모델, 출시 여부 최종 승인

### Product / PM Agent
- 요구사항 정리
- Decision/Spec 관리
- Task 분해
- 우선순위 판단
- Dev Agent 결과 검수

### Research Agent
- 최신 정보 조사
- 출처 확인
- 사실과 해석 분리
- 가정은 가정으로 표시

### Design Agent
- UX Flow, UI, 상태, 접근성, Design System 기준 검토
- 구현 가능한 수준으로 명세

### Development Agent
- 지정 Task 범위만 구현
- 기존 구조 우선
- Test/Build 수행
- 제품 정책 임의 변경 금지

### QA Agent
- 생성자와 분리된 관점으로 AC, Regression, Security, State, Release 조건 검수

## 3. Source of Truth 우선순위
1. Product Owner의 최신 명시 결정
2. 이 파일
3. 최신 유효 Decision
4. Product Policy / Project Brief
5. Architecture / Tech Stack
6. 현재 GitHub Issue
7. CURRENT 요약

충돌하면 위 순서가 우선한다.

## 4. 기본 작업 루프
`Context → Task → Implement → Test → Review → Fix → Done`

Task는 반드시 다음을 가진다.
- Goal
- Why
- Scope
- Out of Scope
- Acceptance Criteria
- Do Not Change
- QA
- Result / Test / Commit

## 5. Decision Gate
다음은 개발 Agent가 임의로 결정하지 않는다.
- 타깃 사용자 변경
- MVP 범위 변경
- 가격/결제 구조 변경
- 개인정보/회원/삭제 정책 변경
- 주요 UX 의미 변경
- Stack 또는 핵심 Architecture 교체

## 6. Ponytail / 최소 변경 원칙
- 가장 작은 변경으로 Task를 해결한다.
- 새 파일, helper, wrapper, class, dependency, abstraction을 만들기 전에 기존 구조로 해결 가능한지 확인한다.
- 미래 확장 대비용 코드를 미리 만들지 않는다.
- 현재 Task와 직접 관계없는 리팩터링 금지.
- 같은 결과라면 더 단순한 구현을 선택한다.

## 7. 완료 정의
`코드가 생김 = 완료`가 아니다.

DONE 조건:
- Acceptance Criteria 충족
- 관련 테스트 통과
- Build/Lint 통과
- Regression 위험 확인
- 미완료/미검증 항목 명시
- 필요 시 실제 사용자/기기 QA 완료

## 8. 문서 운영
- CURRENT에는 최신 상태만 둔다.
- 결정의 이유와 변경 이력은 DECISIONS에 둔다.
- 제품 정책은 PRODUCT_POLICY에 둔다.
- 개발 세부 구현 로그를 제품 정책 문서에 섞지 않는다.

## 9. 보안
- API key, token, private key, password, service account JSON, secret 원문을 GitHub/문서/Issue/Prompt에 기록하지 않는다.
- 민감한 동작은 최소권한과 사람 승인 단계를 둔다.
