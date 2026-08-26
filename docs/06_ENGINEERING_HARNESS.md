# 06 ENGINEERING HARNESS

## 목적
AI 보조 개발에서도 코드베이스가 즉흥적인 바이브코딩 결과물로 무너지지 않게 하는 **개발 안전레일**이다.

이 문서는 주로 `EXECUTION MODE`에서 사용한다.

## 1. 구현 전 Preflight
1. `CURRENT.md`에서 현재 Mode와 우선순위를 확인한다.
2. 현재 Task를 확인한다. 코드 변경 Task라면 GitHub Issue를 기본값으로 한다.
3. 관련 Spec / Decision / Policy를 읽는다.
4. 기존 코드와 패턴을 탐색한다.
5. 기존 dependency / API 존재 여부를 확인한다.
6. Scope / Out of Scope / Do Not Change를 확인한다.
7. Acceptance Criteria와 QA Method를 확인한다.
8. 제품 의미를 바꾸는 모호함이 있으면 구현 전에 중단하고 `DECISION NEEDED`로 올린다.

## 2. Ponytail — 최소 변경 원칙
- 필요한 최소 코드로 해결한다.
- 새 파일 / 클래스 / helper / wrapper / abstraction을 만들기 전에 기존 패턴을 찾는다.
- Task와 무관한 리팩터링을 하지 않는다.
- 미래 확장을 위한 범용화를 미리 만들지 않는다.
- 새 dependency는 기존 도구로 해결 불가능한 경우에만 추가한다.
- 같은 결과라면 더 단순한 구현을 선택한다.

`Ponytail`은 이 프로젝트에서 사용하는 최소 변경 원칙의 별칭이며 공식 업계 표준 용어가 아니다.

## 3. Hallucination 방지
- 존재하지 않는 파일 / 함수 / API를 추측하지 않는다.
- package 버전을 기억으로 정하지 않는다.
- compiler / type error를 suppress로 숨기지 않는다.
- production path에 fake data / TODO / placeholder를 남기지 않는다.
- 공식 문서 또는 현재 코드에서 확인할 수 없는 내용은 `NOT VERIFIED`로 표시한다.

## 4. 변경 범위
### Do
- 현재 Task와 직접 관련된 파일만 수정
- 기존 naming / style / pattern 유지
- 실패 케이스와 상태 고려
- 필요한 test 추가 또는 기존 test 실행
- 변경 후 diff 직접 검토

### Don't
- unrelated cleanup
- 대규모 rename
- architecture 전면 교체
- 제품 정책 변경
- secret commit
- Task 밖의 편의성 리팩터링

## 5. Git Traceability

Execution Mode의 구현은 아래 연결이 남아야 한다.

`Decision / Spec → Task / Issue → Commit / PR / Test → QA`

### 작업 전
- branch 확인
- working tree 확인
- 현재 Task / Issue 확인

### 작업 중
- 하나의 **의미 있는 work cycle**을 하나의 추적 가능한 Commit으로 남긴다.
- 의미 있는 work cycle은 하나의 목적을 가진 검토·테스트 가능한 변경 단위다.
- 채팅 한 번, 파일 저장 한 번마다 Commit하지 않는다.

### 작업 후
- diff 검토
- unrelated change 제거
- Test / Build / Validation
- Task / Issue를 역추적할 수 있는 Commit 메시지
- Result / Tests / Commit / Risk / Not Verified 기록

예:

```text
feat(#14): add bookmark deletion
fix(TSK-021): prevent duplicate save
```

PR은 협업, 리뷰, 위험도가 높은 변경에서 사용한다. 1인 프로젝트의 모든 작은 변경에 강제하지 않는다.

## 6. 최소 품질 Gate
Task 완료 전 최소:
- typecheck 또는 해당 언어의 정적 검증
- lint 또는 코드 품질 검사
- relevant unit / integration test
- production build 또는 이에 준하는 실행 가능성 확인

UI Task라면 추가:
- Default
- Loading
- Empty
- Error
- Success
- Disabled
- Long text
- narrow viewport

프로젝트 특성상 해당되지 않는 항목은 `N/A`로 명시할 수 있다.

## 7. 환경
- dev / staging / production 설정을 필요한 수준에서 분리한다.
- production DB를 일반 개발 테스트 대상으로 사용하지 않는다.
- secret은 환경변수 / secret manager로 관리한다.
- 테스트 데이터와 실제 사용자 데이터를 구분한다.

## 8. 완료 보고
```text
Task / Issue:
Result:
Files changed:
Tests / Validation:
Build:
Commit SHA / Message:
PR:
Known risk:
Not verified:
Handoff to QA:
```

`Not verified`가 있으면 숨기지 않는다.

Development 완료는 구현 완료를 뜻한다. 최종 `DONE`은 필요한 QA가 끝난 뒤 결정한다.
