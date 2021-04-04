# Agile with Redmine

## Background

### * Agile

1. What is Agile? (책 Head First Agile 발췌...)
    Agile is a set of methods and methodologies that are optimized to help with specific problems that software teams run into, and kept simple so they’re relatively straightforward to implement.
These methods and methodologies address all of the areas of traditional software engineering, including project management, software design and architecture, and process improvement. Each of those methods and methodologies consists of practices that are streamlined and optimized to make them as easy as possible to adopt.

    Agile is also a mindset, and that’s a new idea for a lot of people who haven’t worked with agile before. It turns out that each team member’s attitude toward the practices they use can make a huge difference in how effective those practices are. The agile mindset is focused on helping people share information with each other, which makes it much easier for them to make important project decisions (rather than just relying on a boss or project manager to make those decisions). It’s about opening up planning, design, and process improvement to the entire team. To help everyone get into an effective mindset, each agile methodology has its own set of values that team members can use as a guide.

2. [Agile Menifesto(한글)](https://agilemanifesto.org/iso/ko/manifesto.html)
[Agile Menifesto(영어)](https://agilemanifesto.org/iso/en/manifesto.html)

3. [Agile 12 Priciples(한글)](https://agilemanifesto.org/iso/ko/principles.html)
[Agile 12 Priciples(영어)](https://agilemanifesto.org/principles.html)

### * Scrum

가장 대표적인 Agile methodology 이며 Project management 와 Product development 에 중점을 두고 다음과 같은 특징을 갖는다
- Sprint 라는 일정 주기로 반복되는 일련의 process 를 거치며 진행한다.
- 한 번의 Sprint 안에서 Sprint planning, Daily Scrum, Sprint Review, Retrospective 등의 활동을 한다.
- 관찰 -> 적응을 반복하며 **지속적인 개선** 에 가치를 둔다.
- Roles in Scrum team
    - **Product Owner** : **Product Backlog 생성, 우선 순위를 관리** 하며 Product Backlog 의 **세부 사항을 모두 파악** 하여 Development team 에 전달할 수 있는 사람.
    - Scrum Master:  팀이 스크럼을 배우고 적용하여 비즈니스 가치를 획득하도록, 팀이 성공하도록 돕는 것이 주 역할이며, 우리의 경우 Redmine 사용을 도와주는 사람.
    - Development team

### * XP(Extreme Programming)

Agile methodology 중 하나로 다음과 같은 특징을 갖는다
- Scrum 과 유사하게 일정 주기로 반복되는 process 를 거쳐 진행하며
- Scrum 과 달리 programming team 이 그들의 일을 더 잘 할 수 있도록 돕는 것에 초점을 맞춘다.
- Scrum 과 달리 특정 역할을 부여하지 않고 모든 팀원이 모든 일을 다 조금씩 하고, 때에 따라 팀원의 skill 에 맞춰 일을 맡아 진행한다.
- **짝 프로그래밍과 자동화된 build 와 test, 지속적인 통합(CI, Continuous Integration), TDD(Test Driven Development)** 를 지향한다.


### * Lean/Kanban

Lean/Kanban은 Agile의 mindset/tool 중 하나이며 lean의 원칙(principles)은 다음과 같다.
1. Eliminate waste
2. Amplify learning
3. Decide as late as possible
4. Deliver as fast as possible
5. Empower the them
6. Build integrity in
7. See the whole

다른 Agile mindset/practice와 마찬가지로 빠르고 효율적으로 고객에게 작동하는 소프트웨어를 전달하는 것에 중점을 두는데,
다른 점이 있다면 Lean/Kanban은 팀의 work flow 에서 **waste를 줄이는 것** 에 크게 초첨을 맞춘다는 점이다.

7 종류의 waste를 다음과 같이 정의하고 있다.
1. Partially done work
2. Extra processes: Sometimes teams will put a lot of effort into documenting a feature that never gets delivered.
3. Extra features: Sometimes one of team member insists on including extra features that they think are brilliant but which no one asked for.
4. Task switching
5. Waiting
6. Motion(phisically)
7. Defects

## Common Policy

0. 이는 절대적인 것이 아니며 협의를 통해 언제든 변경/추가/삭제할 수 있다.

1. Daily meeting
    - 매일 오후 1시까지 Mattermost 의 해당 프로젝트 'DailyScrum' channel 에 **어제 한 일, 오늘 할 일, 이슈** 에 대해 간략히 공유한다.

2. Work item(issue)
    - Work item 은 **User story** 이거나 **Bug** 이거나 **문서작업** 이어야 한다.
    - User story 는 (개발을 의뢰한)Client 의 요구사항을 반영해 (가능한) 구성원들의 협의를 통해 작성한다.
    - User story 는 다음 형식을 따른다. <누가> <무엇을 했을때> <어떻게 된다>

        ex) 관리자가 진열 상품을 선택해 삭제 버튼을 누르면 해당 상품에서 삭제된다, 회원/비회원이 주문 시 필수 옵션을 선택하지 않고 주문을 하면 주문이 실패한다
    - User story 형식으로 만든 아이템은 추후 **테스트 시나리오** 로 사용할 수 있다.
    - **Tracker** : Redmine issue card 에 추가할 수 있는 필드로, 우리는 해당 work item 의 성격을 구분하기 위해 사용하며 크게 다음과 같다.
        - Feature
        - Bug fix
        - Test
        - Document
        - Not Anymore: 더이상 사용하지 않는 기능
    - **Category** : Redmine issue card 에 추가할 수 있는 필드로, 해당 work item 을 그룹핑하기 위해 사용한다.
        - ex) Order, Sell, Point, etc...

3. Work flow
기본적으로 개발은 [github-flow](https://guides.github.com/introduction/flow/) (Branch 를 생성하여 작업한 뒤 pull request -> merge 하는 방식) 를 따라 진행해 본다. (참고: 명시적 versioning 에 적합한 [git-flow](https://nvie.com/posts/a-successful-git-branching-model/))
권장 [[Git Commit convention]]

    1. Backlog
        - 상단에 위치할 수록 우선 순위가 높다.

    2. In Progress:Develop
        - Backlog column 에 있는 work item 을 pulling 하는 방식으로 진행한다.
        - Pulling 할 때 Assignee 에 자신의 이름을 입력한다.
        - 한 사람이 최대 1개의 item 만 해당 column 에 pulling 한다.
        - 작업이 끝나면 pull request 를 한 뒤 Waiting column 으로 옮긴다.
        - 만약 작업을 끝내지 못하고, 작업을 진행할 수 없는 경우에도 Waiting column 으로 옮긴 뒤 새로운 item 을 가져와 진행한다.
        - Waiting column 으로 옮길 때는 **반드시 Notes 에** 사유를 남기도록 한다. (ex) 서버 작업이 아직 안되서 waiting, pull request wating

    3. In Progress:Waiting
        - Pull Request 를 했거나, 기타 다른 상황으로 인해 개발을 완료하지 못하고 대기해야 하거나, Done? column 에 갔다가 문제를 발견해 다시 개발해야하는 item 이 위치하는 column.

    4. Done?
        - Pull Request 를 통해 (간단한) Code review 후 Merge 가 되면 Done? column 으로 item 을 옮긴다.


4. Sprint
Scrum 에서 이야기하는 일정 주기를 갖고 진행하는 process 이며, 해당 기간 안에 달성할 item 들이 있다.
Redmine 에 Sprint 메뉴가 있지만, Agile board 에서 sprint 로 filtering 이 되지 않으므로,
이것이 가능한 Redmine 의 **Version** 을 Sprint 로 활용한다.

5. Sprint Review
(개발을 의뢰한) Client 와 기타 이해 관계자들과 함께 이번 Sprint 에서 개발한 것을 demo 를 통해 확인한다.
Sprint Review 전에 Done? column 에 있는 item 들을 미리 테스트하는 것을 권장하며, 테스트 시 문제가 없으면 Accepted 로 상태를 변경한다.

6. Retrospective
이번 Sprint 에서 좋았던 점, 개선하면 좋을 점 등을 나누며 이 시간에 지금 읽고 있는 문서를 수정하게 될 것이다.

7. Sprint planning
Product owner 가 새로 시작할 Sprint 에 넣을 item 을 선정하고 (필요하다면) 세부 내용을 설명하며, 각 item 에 story point 를 매긴다.

8. Code Review
    - 코드 리뷰의 목적:
        코드를 좋은 품질로 유지하기 위함
    - 좋은 품질의 코드란?:
        유지 보수가 쉬운 코드
    - 유지 보수가 쉬운 코드란?
        1. 설계 측면에서 기능의 수정, 확장이 쉬운 코드
        2. 가독성 측면에서 코드의 변수명, 함수명 및 주석이 명확하여, 읽었을 때 한 편의 글처럼 술술 읽을 수 있는 코드
        3. 중복 코드가 없고 간결하여 실수할 여지를 줄이는 코드
    - **PR은 작게 작게 할 수 있도록 고민(Branch 작업 할 때, 각 branch 별 의존성을 최소화 할 수 있는 방법을 고민)**
    - 리뷰가 끝나면 작업자가 merge를 하고 Redmine work item을 Done? column으로 옮긴다.
