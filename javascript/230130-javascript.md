# TODAY I LEARNED

## Learned

### let and const

const가 항상 read-only인 것은 아닙니다. 아래처럼 object 안의 변수까지 체크하지는 않습니다.

```javascript
const person = {
	name: "Nicolas"
}

person = true // error
person.name = "Pedro" // changed. no error
```

### Dead Zone

temporal dead zone은 let이랑 같이 소개되는 개념입니다.

let 변수는 초기화하기 전에는 읽거나 쓸 수 없습니다
(선언 구문에 초기 값을 지정하지 않은 경우 undefined로 초기화함).
초기화 전에 접근을 시도하면 ReferenceError가 발생합니다.
* 참고: var 변수와 다른 점으로, var의 경우 선언 전에 접근할 시 undefined입니다.

변수 스코프의 맨 위에서 변수의 초기화 완료 시점까지의 변수는 "시간상 사각지대"(Temporal Dead Zone, TDZ)에 들어간 변수라고 표현합니다.

### 호이스팅

JavaScript에서 호이스팅(hoisting)이란, 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미합니다. var로 선언한 변수의 경우 호이스팅 시 undefined로 변수를 초기화합니다. 반면 let과 const로 선언한 변수의 경우 호이스팅 시 변수를 초기화하지 않습니다.

### Block Scope

let, const의 또 다른 장점은 block scope가 있다는 점입니다.

let, const : block scope (중괄호{} 단위의 범위)
var : function scope (함수 단위의 범위)

