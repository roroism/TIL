# TODAY I LEARNED

## Learned

### IE를 지원하지 않아도 된다면 가장 쓸모 있는

- flex : 박스의 크기, 방향, 순서, 정렬, 간격을 제어하는 새로운 박스 모델.
- flex는 IE에서 버그가 많음.

#### flex

- 아이템 크기를 자동 분배한다. (flex-grow/-shrink/-basis)
- 진행 축 정렬 (justify-content), item들사이의 공간 자동 분배는 auto margin이 아니라 free space 라고 한다.
- 교차 축 정렬 (align-items/-self/-content) align-items : 한 줄, align-self : 한 개, align-content : 여러 줄
- 배치 순서 변경 (order) 활용 예 : html 문서상에 중요한 내용을 먼저 표시하고 화면상에는 중요한 내용을 나중에 표시하게 할 때.
- 감싸기 (flex-direction/-wrap/-flow) : 셀이 행으로 배치되다가 끝에서 줄바꿈 되면서 아래로 떨어지고, 박스 끝에서 아래로 떨어지는 배치에 관여하는 속성.

#### flex 용어

1. flex container(플렉스 컨테이너)
2. flex item(플렉스 아이템)
3. free space(빈 공간)
4. main axis(진행 축)
5. cross axis(교차 축)

##### flex container

- 'display' 속성 값이 'flex' 또는 'inline-flex'인 박스.
- 내부에 흐르는 자식 콘텐츠(엘리먼트, *텍스트 노드*)는 저절로 플렉스 아이템이 된다.
- 플렉스 컨테이너에만 적용 가능한 속성이 있다.

##### flex item

- 플렉스 아이템에만 적용 가능한 속성이 있다.

##### free space

- 플렉스 아이템이 점유하는 영역 (flex-basis, width, height, padding, border, margin)을 제외하고 남은 공간을 프리 스페이스라고 부른다.
- '0, 양수, 음수' 프리 스페이스가 발생할 수 있다.
- *프리 스페이스는 플렉스 아이템의 팽창 지수(flex-grow)와 수축 지수(flex-shrink)를 이용하여 플렉스 아이템으로 분배할 수 있다.*

##### main axis

- 플렉스 아이템 배치 방향으로써 플렉스 컨테이너에 flex-direction 속성을 적용하여 설정할 수 있다.

##### cross axis

- 플렉스 아이템 배치 방향과 직각으로 교차하는 방향으로써 flex-direction 값의 직각 방향.
- 진행 축의 방향에 따라 교차 축이 달라지기 때문에 교차 축은 행이 될 수도 있고 열이 될 수도 있다.
- align-\* 속성의 기준이 되는 축이다.

