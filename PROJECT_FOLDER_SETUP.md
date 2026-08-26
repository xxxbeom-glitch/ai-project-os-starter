# PROJECT FOLDER SETUP GUIDE

이 문서는 `PROJECT_INSTRUCTIONS.md`와 `docs/` 파일을 **ChatGPT Project / Claude Project 같은 프로젝트형 AI 작업공간에 어떻게 넣고 운영할지** 설명하는 사용 가이드다.

## 1. 프로젝트를 하나 만든다

제품 하나당 프로젝트 하나를 기본값으로 둔다.

예:
- LinkPocket
- 여행 예약 서비스
- 익명 커뮤니티 앱

서로 다른 제품을 하나의 Project에 섞지 않는다.

## 2. 상위 지침을 넣는다

`PROJECT_INSTRUCTIONS.md`는 프로젝트 전체의 공통 행동 규칙이다.

플랫폼에 Project Instructions, Custom Instructions, Project Guidelines처럼 지속 지침을 넣을 수 있는 영역이 있다면 이 파일의 핵심 내용을 넣는다.

목적은 다음과 같다.
- 대화마다 제품 방향이 달라지는 것 방지
- 이미 정한 정책을 다시 뒤집는 것 방지
- 역할별 책임 혼선 방지
- 완료 기준 없는 작업 방지
- AI가 모르는 내용을 추측하는 것 방지

## 3. 기준 문서를 프로젝트 자료로 넣는다

`docs/` 폴더는 프로젝트의 공용 기억 장치다.

처음부터 모든 문서를 길게 만들 필요는 없다.

### 최소 시작 세트
- `00_PROJECT_BRIEF.md`
- `03_TECH_STACK.md`
- `05_AGENT_OPERATING_MODEL.md`
- `06_ENGINEERING_HARNESS.md`
- `CURRENT.md`

### 필요할 때 추가
- 정책 이슈가 생기면 `01_PRODUCT_POLICY.md`
- 수익화가 중요하면 `02_BUSINESS_MODEL.md`
- 구조가 복잡해지면 `04_ARCHITECTURE.md`
- 디자인 일관성이 필요하면 `09_DESIGN_SYSTEM.md`
- QA가 커지면 `07_QA_RELEASE_HARNESS.md`
- 결정이 쌓이면 `08_DECISIONS.md`

## 4. 역할별 대화를 나눈다

같은 Project 안에서 대화를 역할별로 나눌 수 있다.

예:
- `01 Product / PM`
- `02 Research`
- `03 Design`
- `04 Development`
- `05 QA`

각 대화는 `roles/`의 해당 역할 파일을 참고한다.

중요한 점은 **각 역할이 서로 다른 목표를 가져도 같은 프로젝트 기준을 사용한다는 것**이다.

## 5. 역할은 자동으로 서로 기억한다고 가정하지 않는다

별도 대화, 별도 Agent, 별도 AI 서비스는 서로의 최신 대화를 자동으로 공유한다고 가정하면 안 된다.

그래서 중요한 결과는 파일로 남긴다.

예:
- 정책 결정 → `08_DECISIONS.md` + `01_PRODUCT_POLICY.md`
- 디자인 기준 변경 → `09_DESIGN_SYSTEM.md`
- 기술 선택 변경 → `03_TECH_STACK.md` + `08_DECISIONS.md`
- 현재 작업 상태 → `CURRENT.md`

즉 **대화는 작업 공간이고, 파일은 프로젝트 기억**이다.

## 6. 한 Task의 기본 흐름

```text
Product / PM
↓ Task 정의
Research
↓ 근거 제공
Design
↓ UX/UI 명세
Development
↓ 구현 결과
QA
↓ PASS / FIX / DECISION NEEDED
Product / PM
↓ 기준 문서와 CURRENT 갱신
```

항상 이 순서를 강제로 사용할 필요는 없다.

단순 문구 수정이라면 Design → QA만 사용할 수도 있다.

## 7. 새 대화 시작 문장 예시

### Product / PM
```text
이 프로젝트의 PROJECT_INSTRUCTIONS와 PROJECT_BRIEF, CURRENT를 기준으로 작업해줘.
이번 역할은 Product/PM이다.
새 기능을 바로 제안하기 전에 현재 목표와 기존 결정 충돌 여부부터 확인해줘.
```

### Design
```text
이 프로젝트의 Product Brief, Product Policy, Design System을 기준으로 작업해줘.
이번 역할은 Design이다.
기능 의미는 임의로 바꾸지 말고, 필요한 제품 결정이 있으면 DECISION NEEDED로 분리해줘.
```

### Development
```text
이 프로젝트의 Tech Stack, Architecture, Engineering Harness와 현재 Task를 기준으로 작업해줘.
이번 역할은 Development다.
현재 Task 범위만 다루고, 제품 정책은 임의로 변경하지 마.
```

### QA
```text
생성자의 설명을 그대로 믿지 말고 독립 QA 역할로 검수해줘.
Acceptance Criteria, 기존 정책, 누락 상태, 회귀 위험, 미검증 항목을 확인하고 PASS / FIX / DECISION NEEDED로 판정해줘.
```

## 8. 매 작업 후 해야 할 것

작업이 끝나면 다음을 확인한다.

- 새로운 제품 결정이 생겼나?
- 정책이 바뀌었나?
- 기술 선택이 바뀌었나?
- 현재 상태가 바뀌었나?
- 다음 역할에 넘길 내용이 있나?

있다면 대화에만 남기지 말고 해당 파일을 갱신한다.

## 9. 파일을 너무 많이 만들지 않는다

파일은 프로젝트 규모에 맞게 합쳐도 된다.

작은 프로젝트라면:
```text
PROJECT_INSTRUCTIONS.md
PROJECT_BRIEF.md
TECH_AND_ARCHITECTURE.md
DESIGN_SYSTEM.md
CURRENT.md
DECISIONS.md
```

정도로도 충분하다.

큰 프로젝트가 되면 역할별로 나눈다.

## 10. 최종 목표

Project Folder의 목적은 AI에게 정보를 많이 먹이는 것이 아니다.

**누가 어느 대화에서 작업하더라도 같은 제품을 만들고 있다는 전제가 유지되게 하는 것**이 목표다.
