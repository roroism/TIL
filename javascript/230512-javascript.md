# TODAY I LEARNED

## Review

### hoisting

- var와 function이 hoisting의 대상입니다.
- hoisting이란 변수의 선언만을 해당 스코프의 맨 위로 끌어올리는 것을 뜻합니다.
- var를 사용한 변수의 선언만 위로 올라갑니다. 값의 초기화는 호이스팅 되지 않습니다.

#### 변수의 호이스팅

- let, const는 호이스팅이 일어나지 않습니다.

#### function의 호이스팅

- 함수의 선언과 값의 초기화는 변수와 다릅니다.
- function은 선언 밖에 없고 선언하는 것 자체가 한 덩어리이여서 값의 초기화는 없는 부분이 됩니다. 하지만 변수는 선언과 초기화가 별개의 부분입니다.

### scope

- let,const : block scope (중괄호{} 단위의 범위)
- var : function scope (함수 단위의 범위)

### closure

- closure는 function과 변수들(환경)의 합.
- closure는 함수가 선언될 때마다 매번 새로 생긴다.

