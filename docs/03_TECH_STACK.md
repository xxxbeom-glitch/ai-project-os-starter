# 03 TECH STACK — LinkPocket

## Platform Decision
MVP는 **반응형 Web App**으로 시작한다.

이유:
- 설치 없이 테스트 가능
- 데스크톱 리서치 사용성과 잘 맞음
- 하나의 코드베이스로 빠르게 검증 가능
- 배포/수정 주기가 짧음

## Stack
- Framework: Next.js
- Language: TypeScript
- UI: React
- Styling: CSS Modules 또는 Tailwind 중 프로젝트 생성 시 하나만 선택
- Backend: Supabase
- Database: PostgreSQL
- Auth: Supabase Auth
- Deploy: Vercel
- Version Control: GitHub

## 선택 기준
기술은 유행보다 다음 순서로 선택한다.
1. 제품 요구를 만족하는가
2. 팀이 유지할 수 있는가
3. 공식 문서와 생태계가 충분한가
4. 배포와 테스트가 단순한가
5. 현재 MVP에 과도하지 않은가

## 변경 Gate
다음은 Architecture Decision이 필요하다.
- Web → Native 전환
- Backend 교체
- DB 교체
- 인증 방식 교체
- 새로운 상태관리/ORM/대형 framework 추가

## 금지
- Agent가 기억에 의존해 package 버전을 추측하지 않는다.
- 같은 역할의 library를 중복 도입하지 않는다.
- 한 Task를 해결하기 위해 Stack 전체를 교체하지 않는다.
