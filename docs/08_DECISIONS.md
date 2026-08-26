# 08 DECISIONS — LinkPocket

이 파일은 **왜 그렇게 결정했는지**를 남긴다. 현재 정책 자체는 각 Spec 문서가 기준이다.

## DEC-001 — MVP는 Web App으로 시작
**Status:** ACTIVE

### Context
작은 팀이 빠르게 사용자 반응을 확인해야 한다.

### Options
- Native mobile app
- Responsive web app

### Decision
Responsive Web App으로 시작한다.

### Why
- 설치 없이 테스트 가능
- 개발/배포 속도가 빠름
- 데스크톱 리서치 행동과 잘 맞음

### Consequence
모바일 네이티브 기능은 MVP 이후 검토한다.

---

## DEC-002 — MVP에는 AI 자동 요약을 넣지 않음
**Status:** ACTIVE

### Context
AI 요약 기능은 매력적이지만 핵심 문제 검증을 흐릴 수 있다.

### Decision
초기에는 링크 저장·정리·재탐색에 집중한다.

### Revisit when
기본 retention이 확인되고, 사용자가 저장 콘텐츠를 다시 찾는 데 실제 불편이 있다는 증거가 생겼을 때.

---

## DEC-003 — Backend는 Supabase
**Status:** ACTIVE

### Why
Auth + PostgreSQL + RLS를 한 서비스에서 빠르게 구성할 수 있고 MVP 규모에 적합하다.

### Guardrail
클라이언트 편의를 이유로 ownership/security를 우회하지 않는다.
