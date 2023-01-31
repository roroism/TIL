# TODAY I LEARNED

## Learned

### Arrow Functions

화살표 함수

화살표 함수 표현(arrow function expression)은 전통적인 함수표현(function)의 간편한 대안입니다.
하지만, 화살표 함수는 몇 가지 제한점이 있고 모든 상황에 사용할 수는 없습니다.

### 'this' in Arrow Function

대부분의 경우에 arrow function을 사용할 수 있습니다.
하지만, this 키워드를 사용해야하는 경우, arrow function을 사용하지 말아야할 때가 있습니다.

아래는 arrow function을 사용하지 말아야하는 두가지 경우입니다.

1. eventlistener에 넘겨주는 callback메소드에서 this사용.
2. 객체 안에서 정의한 함수안에서 this사용.
