# AI Project OS Starter

이 저장소는 **ChatGPT Project 또는 Claude Project 같은 프로젝트형 AI 작업공간에서, 프로젝트의 방향과 규칙이 대화마다 흔들리지 않게 만드는 예시**입니다.

가상의 북마크 웹앱 `LinkPocket`을 예시로 사용합니다.

> 핵심 아이디어: AI에게 매번 처음부터 설명하지 말고, **프로젝트의 목적·정책·기술·역할·작업 방식·QA 기준을 파일로 고정해서 공통 맥락으로 사용한다.**

## 무엇을 배우는 저장소인가

이 저장소의 목적은 코딩 도구 설정이 아닙니다.

새 프로젝트를 정했을 때 먼저 다음을 정리하는 방법을 보여줍니다.

1. 우리는 무엇을 왜 만드는가
2. 누구를 위한 제품인가
3. MVP에서 무엇을 하고 무엇을 하지 않는가
4. 어떤 정책을 지켜야 하는가
5. 어떻게 돈을 벌 것인가
6. 앱인지 웹인지, 어떤 기술로 만들 것인가
7. 폴더와 파일은 어떤 책임으로 나눌 것인가
8. PM / Research / Design / Development / QA 역할은 어떻게 나눌 것인가
9. 역할 간에 어떤 형식으로 인계할 것인가
10. AI가 임의로 제품 방향을 바꾸지 않게 어떤 Do / Don't를 둘 것인가
11. Engineering Harness와 QA Harness를 어떻게 둘 것인가
12. 현재 상태와 과거 결정을 어떻게 분리해 관리할 것인가

## ChatGPT / Claude Project에서 쓰는 방식

### 1. 프로젝트를 하나 만든다
ChatGPT 또는 Claude에서 해당 제품 전용 Project/Workspace를 만든다.

### 2. `PROJECT_INSTRUCTIONS.md`를 프로젝트 상위 지침으로 사용한다
이 파일은 프로젝트 전체에서 계속 유지해야 하는 규칙이다.

플랫폼에 프로젝트 지침 입력란이 있다면 핵심 내용을 넣고, 파일도 프로젝트 자료로 함께 보관한다.

### 3. `docs/`를 프로젝트 지식 파일로 넣는다
모든 파일을 매번 대화에 복사할 필요는 없다. 역할에 따라 필요한 문서를 참조한다.

### 4. 역할별 대화를 나눌 수 있다
예:
- Product / PM 대화
- Research 대화
- Design 대화
- Development 대화
- QA 대화

중요한 점은 대화방 이름이 아니라 **모든 역할이 같은 Source of Truth를 사용한다는 것**이다.

### 5. 대화 자체를 Source of Truth로 만들지 않는다
어떤 대화에서 중요한 결정을 했으면 `DECISIONS.md`, `PRODUCT_POLICY.md`, `CURRENT.md` 같은 기준 파일에 반영한다.

별도 대화나 다른 AI 서비스가 그 내용을 자동으로 공유한다고 가정하지 않는다. **파일이 공용 기억 장치다.**

## 추천 구조

```text
ai-project-os-starter/
├─ README.md
├─ PROJECT_INSTRUCTIONS.md
├─ PROJECT_FOLDER_SETUP.md
│
├─ docs/
│  ├─ 00_PROJECT_BRIEF.md
│  ├─ 01_PRODUCT_POLICY.md
│  ├─ 02_BUSINESS_MODEL.md
│  ├─ 03_TECH_STACK.md
│  ├─ 04_ARCHITECTURE.md
│  ├─ 05_AGENT_OPERATING_MODEL.md
│  ├─ 06_ENGINEERING_HARNESS.md
│  ├─ 07_QA_RELEASE_HARNESS.md
│  ├─ 08_DECISIONS.md
│  ├─ 09_DESIGN_SYSTEM.md
│  ├─ 10_RESEARCH_REFERENCE.md
│  └─ CURRENT.md
│
├─ roles/
│  ├─ PRODUCT_PM.md
│  ├─ RESEARCH.md
│  ├─ DESIGN.md
│  ├─ DEVELOPMENT.md
│  └─ QA.md
│
└─ templates/
   ├─ TASK.md
   ├─ HANDOFF.md
   ├─ DECISION.md
   └─ QA_REPORT.md
```

## 파일별 역할

| 파일 | 쉽게 말하면 |
|---|---|
| `PROJECT_INSTRUCTIONS.md` | 이 프로젝트에서 AI가 항상 지켜야 하는 헌법 |
| `00_PROJECT_BRIEF.md` | 우리는 뭘 왜 만드는가 |
| `01_PRODUCT_POLICY.md` | 서비스가 지켜야 하는 정책 |
| `02_BUSINESS_MODEL.md` | 어떻게 돈을 벌고 무엇을 검증할 것인가 |
| `03_TECH_STACK.md` | 무엇으로 만들 것인가 |
| `04_ARCHITECTURE.md` | 파일과 코드 책임을 어떻게 나눌 것인가 |
| `05_AGENT_OPERATING_MODEL.md` | AI 역할들이 어떻게 협업하는가 |
| `06_ENGINEERING_HARNESS.md` | 개발할 때 사고를 막는 안전레일 |
| `07_QA_RELEASE_HARNESS.md` | 결과가 정말 맞는지 판정하는 기준 |
| `08_DECISIONS.md` | 왜 그렇게 결정했는가 |
| `09_DESIGN_SYSTEM.md` | 디자인 일관성을 유지하는 기준 |
| `10_RESEARCH_REFERENCE.md` | 조사와 레퍼런스 사용 규칙 |
| `CURRENT.md` | 지금 어디까지 왔고 다음은 무엇인가 |
| `roles/*` | 각 역할의 책임과 출력 형식 |
| `templates/*` | Task, Handoff, Decision, QA 작성 양식 |

## Source of Truth 원칙

대화가 많아질수록 가장 중요한 것은 **어떤 정보가 최종 기준인지** 정하는 것입니다.

이 예시는 아래 순서를 사용합니다.

1. 사용자의 최신 명시 결정
2. `PROJECT_INSTRUCTIONS.md`
3. 최신 유효 Decision
4. Product Brief / Product Policy
5. Tech Stack / Architecture / Design System
6. 현재 Task
7. `CURRENT.md`
8. 과거 대화

충돌하면 위쪽이 우선합니다.

## Project OS의 핵심 루프

```text
Goal
↓
Context 확인
↓
Task 정의
↓
담당 Role 실행
↓
Handoff
↓
독립 QA
↓
PASS / FIX / DECISION NEEDED
↓
기준 문서 업데이트
↓
CURRENT 업데이트
```

## 가장 중요한 규칙

- AI의 답변 자체를 프로젝트 결정으로 취급하지 않는다.
- 중요한 결정은 기준 문서에 반영한다.
- 제품 정책을 Development 역할이 임의로 바꾸지 않는다.
- 확실하지 않은 내용은 추측하지 않고 질문 또는 `DECISION NEEDED`로 올린다.
- 큰 일을 한 번에 시키지 않고 Task로 나눈다.
- 생성과 검수를 분리한다.
- 완료 기준 없이 `완료`라고 하지 않는다.
- 새 규칙을 계속 추가하기보다 실제로 반복되는 문제만 규칙으로 승격한다.
- Project Folder의 목적은 문서 수를 늘리는 것이 아니라 **프로젝트의 판단을 일관되게 만드는 것**이다.

## 교육용 추천 순서

처음에는 아래 다섯 개만 보여줘도 충분합니다.

1. `PROJECT_INSTRUCTIONS.md`
2. `docs/00_PROJECT_BRIEF.md`
3. `docs/05_AGENT_OPERATING_MODEL.md`
4. `docs/06_ENGINEERING_HARNESS.md`
5. `docs/CURRENT.md`

그 다음 실제 프로젝트가 복잡해질 때 Policy, Business, Tech, Design, QA 문서를 추가하면 됩니다.
