# 06 ENGINEERING HARNESS

## 목적
AI 보조 개발에서도 코드베이스가 즉흥적인 바이브코딩 결과물로 무너지지 않게 하는 **개발 안전레일**이다.

## 1. 구현 전 Preflight
1. CURRENT 확인
2. 현재 Issue 확인
3. 관련 Spec / Decision 읽기
4. 기존 코드와 패턴 탐색
5. 기존 dependency/API 확인
6. Scope와 Do Not Change 확인
7. 모호한 제품 결정이 있으면 구현 전 중단

## 2. Ponytail — 최소 변경 원칙
- 필요한 최소 코드로 해결한다.
- 새 파일/클래스/helper/wrapper/abstraction 전 기존 패턴을 찾는다.
- Task와 무관한 리팩터링 금지.
- 미래 확장을 위한 범용화 금지.
- 새 dependency는 기존 도구로 해결 불가능한 경우에만 추가한다.

## 3. Hallucination 방지
- 존재하지 않는 파일/함수/API를 추측하지 않는다.
- package 버전을 기억으로 정하지 않는다.
- compiler/type error를 suppress로 숨기지 않는다.
- production path에 fake data/TODO/placeholder를 남기지 않는다.
- 공식 문서 또는 현재 코드에서 확인할 수 없는 내용은 `NOT VERIFIED`로 표시한다.

## 4. 변경 범위
### Do
- 현재 Issue와 직접 관련된 파일만 수정
- 기존 naming/style/pattern 유지
- 실패 케이스와 상태 고려
- 필요한 test 추가

### Don't
- unrelated cleanup
- 대규모 rename
- architecture 전면 교체
- 제품 정책 변경
- secret commit

## 5. Git 규칙
작업 전:
- branch 확인
- working tree 확인

작업 후:
- diff 검토
- unrelated change 제거
- Test/Build
- Task ID가 추적 가능한 commit
- Result/Test/Risk 기록

## 6. 최소 품질 Gate
Task 완료 전 최소:
- typecheck
- lint
- relevant unit/integration test
- production build 가능 여부

UI Task라면 추가:
- Loading
- Empty
- Error
- Success
- Disabled
- Long text / narrow viewport

## 7. 환경
- dev / production 설정을 분리한다.
- production DB를 개발 테스트 대상으로 사용하지 않는다.
- secret은 환경변수/secret manager로 관리한다.

## 8. 완료 보고
```text
Task:
Result:
Files changed:
Tests:
Build:
Commit:
Known risk:
Not verified:
```

`Not verified`가 있으면 숨기지 않는다.
