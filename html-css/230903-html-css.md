# TODAY I LEARNED

## Learned

### display와 position의 비밀

#### Lv3 에서 새로 추가된 값들(flow-root, flex, grid, contents)

##### display: flow-root

- 매우 유용하다.
- 블록 컨테이너가 된다.
- 포함한 float 요소는 컨테이너 끝에서 clear 된다.
- 부모-자식 간의 수직 marin 중첩 현상이 발생하지 않는다.

##### display: flex

- 일반적인 node도 flex아이템이 되지만, text node도 flex아이템이 된다.

##### display: grid

- 2차원 기반으로 배치.

##### 배치 코드 간결함 비교

- display:grid < display:flex < float:left < display:inline-block
- grid가 제일 간결하다.

##### flex와 grid에서 flex만 가능한 배치

- 정리 : flex는 grid와 달리 격자에 구애를 받지 않음.
- grid를 심도있게 공부한다면 완전히 불가능하지는 않지만, 이미 grid로 그려진 셀 안에서는 불가능.

##### flex와 grid에서 grid만 가능한 배치

- 정리 : 셀의 병합 가능
- flex를 심도있게 공부한다면 비슷하게 흉내를 낼수는 있다.

#### position

##### position: static

- 배치 기준 없음. 흐름에 따라 배치.

##### position: relative

- left, right, top, bottom, z-index, inset 속성 사용가능.
- 박스의 현재 위치가 배치의 기준. (방향 속성 사용시 현재의 위치를 기준으로 상대적으로 이동)
- 배치를 변경할 때 다른 박스의 흐름을 깨지 않음.
- 자식 또는 자손 요소의 absolute 배치 기준이 됨.
- inset : left, right, top, bottom 값을 한 번에 선언할 수 있는 단축 속성이다. (작성 순서 : top, right, bottom, left) 그래서 position: absolute에서 inset 값을 0으로 처리한 다음에 margin을 auto로 설정하면 박스를 화면의 한 가운데에 위치시킬 수 있다.

##### position: absolute

- left, right, top, bottom, z-index, inset 속성 사용가능.
- 일반적인 흐름에서 완전히 이탈한다.
- 부모, 형제의 크기나 위치에 전혀 영향을 미치지 않음. (영역을 차지하지 않음)
- 조상 박스가 relative, absolute, fixed, **transform** 일 때 조상 기준으로 배치.

##### position: fixed

- left, right, top, bottom, z-index, inset 속성 사용가능.
- 뷰포트가 배치 기준.
- **조상 요소에 transform 속성이 있으면 transform 속성이 있는 요소가 배치 기준.**

##### position: sticky

- left, right, top, bottom, z-index, inset 속성 사용가능.
- 스크롤 포트가 배치 기준.
- 부모 요소가 스크롤 포트에 보이는 동안 스크롤 포트 기준으로 고정.
- 그리고 부모 요소가 스크롤 밖으로 이탈하면 고정을 멈춤.
- 정리 : 3가지 조건이 필요하다. 1 스크롤 포트라고 불리는 스크롤 바가 있는 박스가 필요. 2 스크롤 포트 안의 자기 자신. 3 스크롤 포트를 감싸는 부모요소.

#### z-index

- z-index의 값은 부모요소의 z-index 값을 넘어서지 못한다.

