# TODAY I LEARNED

## Learned

### display와 position의 비밀

#### display

- inline, block, inline-block, none 이라는 값을 사용할 수 있다.
- Lv3에서 새로 추가된 값들 : flow-root, flex, grid, contents

##### changed display

- display를 바꾸는 속성들이 있다. position: absolute, fixed / float: left, right 는 display 속성을 block으로 바꾼다.
- 이것이 의미하는 바는 가로로 배치되던 것들이 수직으로 배치가 된다는 의미이다.
- 그래서 굳이 display 속성을 block으로 할 필요가 없다.

##### display: inline

- 수직 패딩은 실제로 적용할 수는 있지만 패딩이 다른 요소를 밀어내지는 못한다. 그래서 패딩영역의 background 영역은 표시할 수 있지만 다른 요소를 밀어내지는 못한다.

##### display: block

- 특징 :  수직 마진이 중첩된다.

##### display: inline-block

- 흐름 방향은 inline 처럼 수평이지만, 블록요소처럼 너비 · 높이를 줄 수 있다.
- 수직 마진은 중첩되지 않는다.
- 기본적으로 inline 처럼 렌더링 되기 때문에 줄 간격에 영향을 받는다. line-height 속성에 영향을 받는다.

##### display: none

- 어떤 장치도 표시하거나 접근할 수 없음. (화면x 인쇄x 보조공학기기x 마우스접근x 키보드접근x ...)

##### display: none vs [hidden]

- hidden속성 : 화면에 노출 시키지도 않고, 어떤 장치에도 노출하지 않는다는 의미.
- display: none 과 hidden속성은 결과가 같다.

