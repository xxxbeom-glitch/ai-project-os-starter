# CURRENT — LinkPocket

**Updated:** 2026-08-27

## 현재 단계
ChatGPT / Claude Project Folder용 Project OS 예시 셋업 완료.

실제 제품 코드는 아직 시작하지 않은 교육용 상태다.

## 지금 기준으로 사용하는 파일
- Project-wide rules: `../PROJECT_INSTRUCTIONS.md`
- Project setup: `../PROJECT_FOLDER_SETUP.md`
- Product: `00_PROJECT_BRIEF.md`
- Policy: `01_PRODUCT_POLICY.md`
- Business: `02_BUSINESS_MODEL.md`
- Tech: `03_TECH_STACK.md`
- Architecture: `04_ARCHITECTURE.md`
- Role pipeline: `05_AGENT_OPERATING_MODEL.md`
- Engineering Harness: `06_ENGINEERING_HARNESS.md`
- QA/Release: `07_QA_RELEASE_HARNESS.md`
- Decisions: `08_DECISIONS.md`
- Design: `09_DESIGN_SYSTEM.md`
- Research: `10_RESEARCH_REFERENCE.md`

## 현재 교육용 Task
`TSK-001 — LinkPocket MVP 첫 구현 Task 정의`

### Goal
Project Brief와 Tech Stack을 기준으로 첫 구현 단위를 정의한다.

### Task Flow
1. Product / PM이 Task 정의
2. Design이 필요한 UI 상태 정의
3. Development가 구현 계획/결과 작성
4. QA가 독립 검수
5. PASS면 CURRENT 갱신

### Acceptance Criteria
- Goal / Why / Scope / Out of Scope 명확
- Product Brief와 충돌 없음
- Tech Stack과 충돌 없음
- Design 상태 기준 포함
- Do Not Change 포함
- QA 방법 포함

### Do Not Change
- Product concept
- MVP 범위
- 수익모델
- Platform = Web
- 현재 확정 Stack

## Blocker
없음.

## 다음 Role
`Product / PM`

`roles/PRODUCT_PM.md`와 `templates/TASK.md`를 사용해 TSK-001을 작성하는 것이 다음 예시 단계다.

## 이 파일의 운영 규칙

`CURRENT.md`는 과거 일기를 쌓는 곳이 아니다.

항상 다음만 짧게 유지한다.
- 현재 단계
- 현재 Task
- 현재 Blocker
- 다음 Role
- 바로 다음 행동

과거의 완료 과정과 이유는 Decision / Task / Handoff에 남긴다.
