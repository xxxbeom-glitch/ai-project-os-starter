# 04 ARCHITECTURE — LinkPocket

## 목표
AI가 기능마다 임의의 구조를 새로 만들지 않도록 기본 경계를 먼저 정한다.

## 권장 시작 구조
```text
src/
├─ app/
├─ features/
│  ├─ auth/
│  ├─ bookmarks/
│  ├─ categories/
│  └─ search/
├─ components/
│  ├─ ui/
│  └─ shared/
├─ lib/
│  ├─ supabase/
│  ├─ validation/
│  └─ utils/
├─ styles/
└─ types/
```

## 원칙
- feature 중심으로 코드를 찾기 쉽게 한다.
- 공용 component는 실제 2곳 이상에서 재사용될 때 승격한다.
- 서버 접근은 공통 client/boundary를 통한다.
- UI 안에 직접 DB query를 흩뿌리지 않는다.
- 인증/ownership은 서버 정책을 우선한다.
- 작은 프로젝트에 과도한 layer를 강제하지 않는다.

## File Responsibility
- `app/`: routing과 page composition
- `features/`: 사용자 기능 단위 로직/UI
- `components/ui`: 공용 UI primitive
- `components/shared`: 여러 feature에서 쓰는 조합 component
- `lib/supabase`: client/server 연결
- `lib/validation`: 입력 검증
- `types`: 공용 domain type

## Do
- 기존 feature 패턴을 먼저 찾는다.
- 파일 이름만 보고 책임을 이해할 수 있게 한다.
- 새로운 공용 abstraction은 실제 반복이 생긴 뒤 만든다.

## Don't
- 한 파일에 UI, DB, policy logic을 모두 넣지 않는다.
- `utils.ts` 하나에 모든 helper를 몰아넣지 않는다.
- 작은 기능마다 별도 service/repository/usecase layer를 기계적으로 만들지 않는다.
- 폴더 구조를 Task마다 바꾸지 않는다.
