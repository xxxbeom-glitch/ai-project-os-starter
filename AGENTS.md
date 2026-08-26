# AGENTS.md

이 저장소를 처음 여는 AI Agent는 아래 순서로 읽는다.

1. `PROJECT_INSTRUCTIONS.md`
2. `docs/CURRENT.md`
3. 현재 GitHub Issue
4. Issue가 링크한 `PROJECT_BRIEF / POLICY / TECH / ARCHITECTURE / DECISIONS`
5. 필요한 Harness와 Cursor Rule

## Project
- Example product: **LinkPocket**
- Type: Web App
- Goal: 링크 저장과 재탐색을 빠르게 만드는 작은 북마크 서비스
- Stack: Next.js + TypeScript + Supabase + Vercel

## Source of Truth
- 방향: `docs/00_PROJECT_BRIEF.md`
- 정책: `docs/01_PRODUCT_POLICY.md`
- 수익: `docs/02_BUSINESS_MODEL.md`
- 기술: `docs/03_TECH_STACK.md`
- 구조: `docs/04_ARCHITECTURE.md`
- Agent 협업: `docs/05_AGENT_OPERATING_MODEL.md`
- Engineering Harness: `docs/06_ENGINEERING_HARNESS.md`
- QA/Release: `docs/07_QA_RELEASE_HARNESS.md`
- Decision history: `docs/08_DECISIONS.md`
- Design System: `docs/09_DESIGN_SYSTEM.md`
- 현재 상태: `docs/CURRENT.md`

## Absolute Rules
- 제품 정책을 임의로 바꾸지 않는다.
- 현재 Task 밖의 변경을 하지 않는다.
- 코드를 쓰기 전에 기존 구조와 관련 파일을 읽는다.
- 새 abstraction보다 기존 패턴 재사용을 우선한다.
- 결과 생성만으로 완료 처리하지 않는다. Test/QA evidence가 필요하다.
- 모호한 제품 결정은 `DECISION NEEDED`로 올린다.
- 비밀키와 인증정보를 Repo/Issue/Prompt에 남기지 않는다.
