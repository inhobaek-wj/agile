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


1.  Product Backlog
	- 우선순위가 있는 비즈니스 가치를 담고 있는 요구사항 목록.
	- 고객이 원하는 것을 고객의 용어로 설명한 것.
	- Product Owner가 관리하며 각 story를 이해하고 있어야 한다.
	- Sprint planning meeting 전에 정리해놓아야 한다. -> 우선 순위, 대략의 Done 기준.
	- 개발시간(story point) 추정은 develop teem이 하며 이것은 팀의 고유 권한이다.
	- Redmine에서
		- 부모 project에서 만들고 Tracker를 Story 로 설정한다.

2. Sprint planning meeting
	- 필수 참석자: Product Owner, Scrum Master, Develop team
	- 다음 사항을 논의하거나 정해야 한다.
		- (비즈니스 가치를 내포한) Sprint 목표.
		- 오는 Sprint의 기간을 정한다.
			- Redmine에서 기간에 맞게 version을 생성한다.
		- 각 Story의 Done을 최대한 명확히 한다.
		- Sprint backlog(task)를 만들어 story point를 추정한다.
			- Redmine에서 자식 프로젝트에 만들고 Tracker를 Feature로 설정한다.
			- 각 task의 시작 날짜, 종료 날짜 version을 sprint에 맞게 설정한다.
		- 참여하는 팀원 목록 및 참여 수준을 고려한 팀의 추정 속도.
		- Story point와 팀의 추정 속도를 바탕으로 이번 sprint에서 작업할 story 선정.
	- Meeting이 끝나면 Scrum master가 Mattermost Agile channel에 요약해 올린다.

3. Daily scrum meeting
	- 필수 참석자: Develop team
    - 팀은 매일 정해진 시간에 15분동안 **어제 한 일, 오늘 할 일, 이슈** 에 대해 간략히 공유한다.

4. Sprint Review meeting
	- 필수 참석자: Product Owner, Scrum Master, Develop team
	- 그외 참석자: 프로젝트 관계자들
	- 목적: 팀과 Product Owner가 현재 상황을 파악하고, 조언을 구하는 등 서로 깊은 대화를 나누기 위함.
		- 이 시간을 통해 Product owner는 제품이나 팀이 지금 어떻게 진행되고 있는지 알게 되고, 팀은 시장과 비즈니스에 어떤 일이 진행되고 있는지 알게 된다.

5. Sprint Retrospective meeting
	- 필수 참석자: Scrum Master, Develop team
	- 다음 사항을 함께 이야기한다.
		- Sprint 결과.
		- 이번 스프린트에서 우리 팀이 잘한 일.
		- 이번 스프린트에서 우리 팀이 부족했던 점.
		- 다음 스프린트에서 우리 팀이 개선하면 좋을 점.
	- Meeting이 끝나면 Scrum master가 Mattermost Agile channel에 요약해 올린다.


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

## With Redmine

1. Project setup
    - 부모 project - 자식 프로젝트로 구조로 구성하고,
    - 자식 프로젝트는 repository 별로 만든다.

2. Product backlog
    - 부모 project에서 만들고 Tracker를 Story 로 설정하고 story라고 부른다.
        - **Tracker** : Redmine issue card 에 추가할 수 있는 필드로, 우리는 해당 work item 의 성격을 구분하기 위해 사용하며 크게 다음과 같다.
	- Product Owner가 관리하며 각 story를 이해하고 있어야 하며,
	- Sprint planning meeting 전에 정리해놓아야 한다. -> 우선 순위, 대략의 Done 기준.
    - description에 Done의 기준 또는 시나리오를 다음 형식으로 적는다. <누가> <무엇을 했을때> <어떻게 된다>
        ex) 관리자가 진열 상품을 선택해 삭제 버튼을 누르면 해당 상품에서 삭제된다, 회원/비회원이 주문 시 필수 옵션을 선택하지 않고 주문을 하면 주문이 실패한다

3. Sprint backlog
    - Sprint planning meeting 때 product backlog를 develop team이 task 단위로 나누어 자식 project에 만든다.
    - 이때, Story point도 추정한다.
    - 다음과 같은 tracker를 가질 수 있으며 task라고 부른다.
        - Feature
        - Bug fix
        - Test
    - 개발 시 참고 사항 등을 description에 적는다.
    - 개발 시 checklist를 활용하면 진행 상황을 파악하는데 도움이 된다.

4. Agile board
- 다음은 Redmine agile board의 각 column에 대한 설명이다.

    1. Backlog
        - 아직 구현 전인 task가 쌓여있다.
        - 상단에 위치할 수록 우선 순위가 높다.

    2. In Progress:Develop
        - 현재 진행중인 task가 쌓여있다.
        - Backlog column 에 있는 task를 작업자가 가져와서 일을 진행한다.
        - 작업자는 해당 task를 가져올 때 Assignee 에 자신의 이름을 입력한다.
        - 한번에 단 1개의 task만 작업하자.
        - 작업이 끝나고 pull request 를 한 뒤 Waiting column 으로 옮긴다.
        - 만약 작업을 끝내지 못하고, 작업을 진행할 수 없는 경우에도 Waiting column 으로 옮긴 뒤 새로운 item 을 가져와 진행한다.
        - Waiting column 으로 옮길 때는 **반드시 Notes 에** 사유를 남기도록 한다. (ex) 서버 작업이 아직 안되서 waiting, pull request wating

    3. In Progress:Waiting
        - Pull Request 를 했거나, 기타 다른 상황으로 인해 개발을 완료하지 못하고 대기해야 하거나, Done? column 에 갔다가 문제를 발견해 다시 개발해야하는 item 이 위치하는 column.

    4. Done?
        - Pull Request 를 통해 Code review 후 Merge 가 되면 Done? column 으로 item 을 옮긴다.

    5. On hold
        - PR이 아닌 다른 사유로 대기중인 task들.


## 그외 준수 사항

1. 기본적으로 개발은 [github-flow](https://guides.github.com/introduction/flow/) (Branch 를 생성하여 작업한 뒤 pull request -> merge 하는 방식) 를 따라 진행해 본다. (참고: 명시적 versioning 에 적합한 [git-flow](https://nvie.com/posts/a-successful-git-branching-model/))
권장 [[Git Commit convention]]


2. Code Review
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
