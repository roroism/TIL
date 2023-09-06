# TODAY I LEARNED

## Learned

### 레이아웃, 여백의 비밀

#### margin

##### 수직 마진 병합

- 인접 형제, 부모/자식. 2가지 경우에서 발생.
- 부모/자식의 경우 자식의 margin 값을 부모가 빼앗아서 사용하는 듯한 렌더링을 보여준다.

##### 수직 마진 병합 규칙

- 블럭 요소 사이에서만 발생.
- 양수끼리, 음수끼리 만난 경우 절대값이 큰 값 적용.
- 양수와 음수가 만난 경우 두 값의 합.

##### 수직 마진 병합 규칙 예외

- 최상위 요소(body)의 수직 마진.
- display: flow-root 인 경우에는 수직 마진 병합 규칙이 발생하지 않는다. (예를 들어 부모에 flow-root를 적용하면 자식의 margin을 가져오지 않는다.)
- 부모의 overflow : hidden | auto | scroll
- 부모의 padding-top/bottom 값이 0 아닌.
- 부모의 border-top/bottom 값이 0 아닌.
- display : inline | inline-\*
- float : left | right

##### 수직 마진을 병합하는 이유?

- 필요이상으로 과도한 margin이 서로 발생하는 것을 상쇄하려는 목적을 가지고 있다.

