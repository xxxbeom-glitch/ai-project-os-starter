# CURRENT — AI Project OS Starter

**Updated:** 2026-08-27

## 현재 단계
`Starter v1.0 — READY`

ChatGPT / Claude Project Folder + GitHub + 개발 도구를 함께 사용할 수 있는 **AI Project Bootstrap / Project OS 교육용 기본 템플릿** 정리가 완료되었다.

이 Repository는 실제 제품 코드베이스가 아니라 새 프로젝트를 시작할 때 복사해서 사용하는 예시다.

## 현재 Mode
`BOOTSTRAP TEMPLATE`

새 프로젝트에 복사한 뒤 `PROJECT_BOOTSTRAP.md`를 실행하고, 사용자 승인 후 `Project OS v0.1`을 만들면 해당 프로젝트가 `EXECUTION MODE`로 전환된다.

## Canonical Source
`GitHub Repository`

ChatGPT / Claude Project에 업로드한 파일은 Snapshot이며, GitHub 최신본과 충돌하면 GitHub가 우선한다.

## 현재 기준 파일
- Project-wide rules: `../PROJECT_INSTRUCTIONS.md`
- Bootstrap protocol: `../PROJECT_BOOTSTRAP.md`
- Project setup guide: `../PROJECT_FOLDER_SETUP.md`
- Product: `00_PROJECT_BRIEF.md`
- Policy: `01_PRODUCT_POLICY.md`
- Business: `02_BUSINESS_MODEL.md`
- Tech: `03_TECH_STACK.md`
- Architecture: `04_ARCHITECTURE.md`
- Role pipeline: `05_AGENT_OPERATING_MODEL.md`
- Engineering Harness: `06_ENGINEERING_HARNESS.md`
- QA / Release: `07_QA_RELEASE_HARNESS.md`
- Decisions: `08_DECISIONS.md`
- Design: `09_DESIGN_SYSTEM.md`
- Research: `10_RESEARCH_REFERENCE.md`

## Starter의 운영 모델

```text
BOOTSTRAP MODE
사용자 인터뷰
→ 기준 문서 작성
→ Cross-document QA
→ 사용자 승인
→ Project OS v0.1

EXECUTION MODE
Task / GitHub Issue
→ Implementation
→ Commit / Test Evidence
→ Independent QA
→ PASS / FIX / DECISION NEEDED
→ Close
→ CURRENT update
```

## Git Traceability
Execution Mode의 코드 변경은 다음 연결을 기본값으로 한다.

`Decision / Spec → Task / Issue → Commit / PR / Test → QA`

- 하나의 의미 있는 work cycle은 하나의 추적 가능한 Commit으로 남긴다.
- 채팅 한 번마다 Commit하지 않는다.
- Commit / PR에서 Task / Issue를 역추적할 수 있어야 한다.
- 구현 완료와 최종 QA PASS를 구분한다.

## 다음 행동
이 Starter 자체에는 추가 기능 작업이 없다.

실제 사용 시:
1. 새 프로젝트용 Repository로 복사
2. LLM에게 `README → PROJECT_INSTRUCTIONS → PROJECT_BOOTSTRAP` 순서로 읽게 함
3. 사용자 인터뷰 진행
4. LinkPocket 예시 내용을 실제 프로젝트로 교체
5. Cross-document QA
6. 사용자 승인
7. Project OS v0.1 확정
8. 첫 Execution Task / GitHub Issue 생성

## Blocker
없음.

## 이 파일의 운영 규칙
`CURRENT.md`는 과거 일기를 쌓는 곳이 아니다.

항상 다음만 유지한다.
- 현재 단계 / Mode
- 현재 Task 또는 목적
- 현재 Blocker
- 바로 다음 행동

과거의 결정은 `DECISIONS`, 작업 이력은 Task / Issue, 구현 증거는 Commit / Test에 남긴다.
