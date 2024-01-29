# TODAY I LEARNED

## 복습

### 선언과 표현 그리고 호이스팅

- 함수 선언문과 함수 표현식의 차이
    - function 키워드로 시작하는지? const 나 let으로 선언된 변수에 할당 연산자를 통해서 함수가 들어가는지의 차이.

```javascript
// 함수(Function)

// 함수 선언문 (Declaration)
function hello() {}

// 함수 표현식 (Expression)
const hello = function() {}
```

#### 호이스팅

- 함수 선언에서는 호이스팅이라는 현상이 발생합니다.
- 함수가 선언되어져 있는 코드를 선언된 부분 안(유효한 범위 안)에서 제일 위로 끌어 올려서 동작하는 개념입니다.

```javascript
// 호이스팅 (Hoisting)

function hello() {
  console.log('Hello~');
}

hello(); // Hello~

// ------------------------------------
// 위(hello)와 아래(hello2)의 함수는 모두 잘 동작합니다.

hello2(); // Hello~

function hello2() {
  console.log('Hello~');
}
```

만약 아래처럼 작성하면 ReferenceError가 발생합니다.

```javascript
hello();

// 호이스팅 되지 않음
const hello = function () {
  console.log('Hello~');
}
```

추가로 아래처럼 작성하면,

```javascript
// world(); // error : 초기화되지 전에 접근 불가

const world = function hello() {
  console.log('Hello~');
}

// hello(); // error : hello를 찾을 수 없음
world(); // Hello~
```

#### 정리

- 간단하게 생각해보면, 익명함수에 상관없이 어떤 함수이든 할당연산자를 통해서 변수에 함수를 할당하면 함수 표현식이되고
- 할당 연산자를 사용하지 않고 function 키워드를 사용해서 이름이 있다면 함수 선언문이 됩니다.
- 함수 선언문은 호이스팅 현상이 발생합니다.
