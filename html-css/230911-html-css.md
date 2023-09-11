# TODAY I LEARNED

## Learned

### IE를 지원하지 않아도 된다면 가장 쓸모 있는

#### 플렉스 아이템의 방향과 순서

- flex-direction : 아이템의 흐름 방향 설정.
- flex-wrap : 박스 끝에 아이템이 도달했을 때, 줄바꿈을 할 것인지 설정.
- flex-flow : flex-direction 과 flex-wrap의 단축형. 실무에서는 거의 flex-flow만 사용한다.
- order : flex아이템의 순서를 정렬할 수 있는, 순서를 변경할 수 있는 속성이다.

##### flex-direction

- 플렉스 아이템의 진행 방향.

##### flex-wrap

- 플렉스 아이템의 줄 바꿈 설정.
- 초기 값 : nowrap (줄 바꿈이 자동으로 안 됨)
- 줄 바꿈을 하려면 wrap 또는 wrap-reverse 로 설정하면 된다.

##### flex-flow

- 초기값 : row nowrap

##### order

- 플렉스 아이템의 배치 순서.
- 값 : `<integer>` // 0, 양의 정수, 음의 정수
- 초기 값 : 0
- order의 값은 상대적이다. 예를 들어서 어떤 아이템이 1이라는 값을 가지고 있다면, 다른 요소의 값보다 높은지 낮은지 판단하여 배치 순서를 바꿔준다.

#### 플렉스 아이템의 정렬과 간격

- justify-content
- align-items
- align-self
- align-content
- gap

##### justify-content

- 진행축 정렬에 관여하는 단 하나의 속성
- 실무에서 가장 많이 사용하는 값은 center와 space-between
- 초기 값 : flex-start (보통 화면 왼쪽으로 쏠려서 배치가 된다.)

##### align-items

- 플렉스 아이템이 한 줄일 때 교차 축 정렬.
- 자주 사용하는 값 : center, stretch
- 초기 값 : stretch // 아이템을 교차 축으로 잡아 늘림.

##### align-self

- 플렉스 아이템의 독립적(1개) 교차 축 정렬.
- 자주 사용하는 값 : center, flex-start, flex-end
- 초기 값 : auto // 컨테이너의 align-items 값을 상속 받음.
- 적용 : 플렉스 아이템

##### align-content

- 플렉스 아이템의 여러 줄 교차 축 정렬과 간격. (align-items는 한 줄 교차 축 정렬)
- 자우 사용하는 값 : center, space-between
- 초기값 : stretch // 줄 간격을 교차 축으로 균등하게 늘림.
- 적용 : '여러 줄' 플렉스 컨테이너

##### gap

- 딱히 flex에서만 사용할 수 있는 값은 아니다. 다중 컬럼, 플렉스, 그리드 아이템 사이의 간격에 사용된다.
- 값 : `<'row-gap'> <'column-gap'>?` // column-gap을 생략하면 자동으로 row-gap이 column-gap이 된다.
- 적용 : 컬럼/플렉스/그리드 컨테이너
- flex-grow나 flex-shrink를 사용한다면 플렉스 컨테이너에 아이템들을 꽉 차게 채울 수 있지만, 만약 정확하게 원하는 gap 크기가 있다면 gap이 도움이 된다.

