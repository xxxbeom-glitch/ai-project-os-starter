# 09 DESIGN SYSTEM — LinkPocket

## 목적
화면마다 다른 판단을 반복하지 않고, UI를 일관된 기준으로 만든다.

## 기본 원칙
- 읽기 쉬운 정보 위계
- 과도한 장식보다 빠른 탐색
- 핵심 CTA는 명확하게
- 상태 변화가 눈에 보여야 함
- 모바일/데스크톱 모두 기본 사용 가능

## Tokens
예시는 개념만 정의한다. 실제 값은 구현 시 한곳에서 중앙관리한다.

- Color: background / surface / text / muted / primary / danger / success
- Typography: display / title / body / label / caption
- Spacing: 4 / 8 / 12 / 16 / 24 / 32 / 48
- Radius: small / medium
- Border: default / focus / error

## Component 우선순위
- Button
- Input
- Search field
- Select / Category chip
- Bookmark item
- Empty state
- Toast / Inline feedback
- Dialog

## 상태 규칙
모든 핵심 인터랙션은 필요한 경우 다음 상태를 검토한다.
- Default
- Hover / Pressed
- Focus
- Disabled
- Loading
- Error
- Success
- Empty

## Do
- 같은 역할의 Component는 같은 token 사용
- 텍스트가 길어져도 레이아웃이 깨지지 않게 설계
- keyboard focus와 접근성 label 확인

## Don't
- 화면마다 임의 색/spacing/radius 생성
- 같은 Button/Input을 복붙해 변종 생성
- Loading/Error/Empty를 디자인 이후 개발자에게 떠넘김

## Design QA 질문
1. 이 화면에서 사용자의 다음 행동이 보이는가?
2. 실패했을 때 무엇을 해야 하는지 알 수 있는가?
3. 데이터가 없을 때 화면이 성립하는가?
4. 좁은 화면과 긴 텍스트에서도 성립하는가?
5. 구현 가능한 규칙으로 정의돼 있는가?
